# amq-stream1.4-execute-local-pc
ローカルPCでAMQ Streamを動かしてみた[Mac]

## 前提条件

Apache KafkaのQuick Startの内容がそのまま、AMQ Streamのインストーラーで実行出来ることの確認

参考：https://kafka.apache.org/quickstart


## 実行

１. レッドハットカスタマーポータルよりインストーラーをダウンロードする。

amq-streams-1.4.0-bin.zip

２. ダウンロードしたzipファイルを任意の場所に展開する
/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005

３. コマンドプロンプトより、zookeeperが必要なため起動する。

```
% cd <HOME>/mylabs/kafka_2.12-2.4.0.redhat-00005
% bin/zookeeper-server-start.sh config/zookeeper.properties
〜省略
[2020-03-29 16:46:00,987] INFO Using checkIntervalMs=60000 maxPerMinute=10000 (org.apache.zookeeper.server.ContainerManager)
```

４. 別コマンドプロンプトより、kakfaを起動する。

```
% cd <HOME>/mylabs/kafka_2.12-2.4.0.redhat-00005
% bin/kafka-server-start.sh config/server.properties
〜省略
[2020-03-29 16:47:35,012] INFO [KafkaServer id=0] started (kafka.server.KafkaServer)
```

５. 別コマンドプロンプトで単一のパーティションと1つのレプリカのみを持つ「test」という名前のトピックを作成する。

```
% cd <HOME>/mylabs/kafka_2.12-2.4.0.redhat-00005
% bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test
```

６. 作成したトピックを確認する。
```
% bin/kafka-topics.sh --list --bootstrap-server localhost:9092
test
```

７. プロデューサーを実行し、コンソールにいくつかのメッセージを入力してKafkaサーバーに送信します。
※Topicを作成したコマンドプロンプト

```
% bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
>first hoge
>first foo
>first bar
```

８. コンシューマを実行し、プロデューサーが送信したメッセージを受信し、標準出力へ出力する。
※別プロンプトで実行

```
% cd <HOME>/mylabs/kafka_2.12-2.4.0.redhat-00005
% bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
first hoge
first foo
first bar
```


## マルチブローカーを使用したメッセージの送受信

１. ブローカー毎の設定ファイルを作成する。
※先程使用したプロデューサーもしくはコンシュマーのコマンドプロンプトを使用する。
※zookeeperとkafkaのプロンプトはそのままにして、プロセスが起動している状態とする。

```
% cp config/server.properties config/server-1.properties
% cp config/server.properties config/server-2.properties
```

２. 同一PCで複数のブローカーを起動するため、ノードやポート、ログディレクトリが重複しないように編集する。

```
% vi config/server-1.properties:
    broker.id=1
    listeners=PLAINTEXT://:9093
    log.dirs=/tmp/kafka-logs-1
 
% config/server-2.properties:
    broker.id=2
    listeners=PLAINTEXT://:9094
    log.dirs=/tmp/kafka-logs-2
```

３. 別プロンプトで上記編集したサーバープロセスを起動し、計3つのKafkaサーバーを起動する。

```
% bin/kafka-server-start.sh config/server-1.properties &
% bin/kafka-server-start.sh config/server-2.properties &
```


４. 複数係数[replication-factor]が3の新しいトピックを作成する。

```
% bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 3 --partitions 1 --topic my-replicated-topic
```

５. 作成したトピックを確認する。

```
% bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic my-replicated-topic
Topic: my-replicated-topic	PartitionCount: 1	ReplicationFactor: 3	Configs: segment.bytes=1073741824
	Topic: my-replicated-topic	Partition: 0	Leader: 2	Replicas: 2,1,0	Isr: 2,1,0
```

出力の説明です。最初の行はすべてのパーティションの概要を示し、追加の各行は1つのパーティションに関する情報を示します。このトピックにはパーティションが1つしかないため、1行しかありません。

「リーダー」は、指定されたパーティションのすべての読み取りと書き込みを担当するノードです。各ノードは、パーティションのランダムに選択された部分のリーダーになります。
「レプリカ」は、リーダーであるかどうかに関係なく、このパーティションのログを複製するノードのリストです。
「isr」は「同期」されたレプリカのセットです。これは、現在有効でリーダーに追いついているレプリカリストのサブセットです。
この例では、ノード2がトピックの唯一のパーティションのリーダーであることに注意してください。

６. 新しく作成したトピックにメッセージを送信[publish]する。

```
% bin/kafka-console-producer.sh --broker-list localhost:9092 --topic my-replicated-topic
>second hoge
>second foo
>second bar
```

７. メッセージを受信する。

```
% bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --from-beginning --topic my-replicated-topic
second hoge
second foo
second bar
```

８. フォールトトレランスをテストする。ブローカー2がリーダーとして機能していたので、プロセスを殺す。

```
% ps aux | grep server-2.properties
% kill -9 <プロセスID>
% ps aux | grep server-2.properties
kmurakat          9641   0.0  0.0  4271368    688 s002  R+    5:29PM   0:00.01 grep server-2.properties
```

９. リーダーがフォロワーの1人に切り替わり、ノード2は同期レプリカセットに存在しなくなった。
```
% bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic my-replicated-topic
Topic: my-replicated-topic	PartitionCount: 1	ReplicationFactor: 3	Configs: segment.bytes=1073741824
	Topic: my-replicated-topic	Partition: 0	Leader: 1	Replicas: 2,1,0	Isr: 1,0
kmurakat@kmurakat-mac kafka_2.12-2.4.0.redhat-00005 % 
```

１０. メッセージを送信する。※元のリーダーがダウンしてもメッセージは送信出来る。
```
% bin/kafka-console-producer.sh --broker-list localhost:9092 --topic my-replicated-topic
>thrid hoge
>third foo
>third bar
```

１１. メッセージを受信する。※元のリーダーがダウンしてもメッセージは受信出来る。
```
% bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --from-beginning --topic my-replicated-topic
thrid hoge
third foo
third bar
```

## kafka Connectの使用

TBD

