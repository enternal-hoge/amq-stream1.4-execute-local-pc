# amq-stream1.4-execute-local-pc
ローカルPCでAMQ Streamを動かしてみた[Mac]

参考：https://kafka.apache.org/quickstart

1. レッドハットカスタマーポータルよりインストーラーをダウンロードする。

amq-streams-1.4.0-bin.zip

2. ダウンロードしたzipファイルを任意の場所に展開する
/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005

3. コマンドプロンプトより、zookeeperが必要なため起動する。

```
% cd /Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005
% bin/zookeeper-server-start.sh config/zookeeper.properties
[2020-03-29 16:46:00,850] INFO Reading configuration from: config/zookeeper.properties (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2020-03-29 16:46:00,851] WARN config/zookeeper.properties is relative. Prepend ./ to indicate that you're sure! (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2020-03-29 16:46:00,855] INFO clientPortAddress is 0.0.0.0:2181 (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2020-03-29 16:46:00,855] INFO secureClientPort is not set (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2020-03-29 16:46:00,857] INFO autopurge.snapRetainCount set to 3 (org.apache.zookeeper.server.DatadirCleanupManager)
[2020-03-29 16:46:00,857] INFO autopurge.purgeInterval set to 0 (org.apache.zookeeper.server.DatadirCleanupManager)
[2020-03-29 16:46:00,857] INFO Purge task is not scheduled. (org.apache.zookeeper.server.DatadirCleanupManager)
[2020-03-29 16:46:00,857] WARN Either no config or no quorum defined in config, running  in standalone mode (org.apache.zookeeper.server.quorum.QuorumPeerMain)
[2020-03-29 16:46:00,858] INFO Log4j found with jmx enabled. (org.apache.zookeeper.jmx.ManagedUtil)
[2020-03-29 16:46:00,869] INFO Reading configuration from: config/zookeeper.properties (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2020-03-29 16:46:00,869] WARN config/zookeeper.properties is relative. Prepend ./ to indicate that you're sure! (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2020-03-29 16:46:00,870] INFO clientPortAddress is 0.0.0.0:2181 (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2020-03-29 16:46:00,870] INFO secureClientPort is not set (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2020-03-29 16:46:00,870] INFO Starting server (org.apache.zookeeper.server.ZooKeeperServerMain)
[2020-03-29 16:46:00,872] INFO zookeeper.snapshot.trust.empty : false (org.apache.zookeeper.server.persistence.FileTxnSnapLog)
[2020-03-29 16:46:00,901] INFO Server environment:zookeeper.version=3.5.7-d01ffa89069093d4dd53c9748f2bddf8aee769cd, built on 02/18/2020 15:07 GMT (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,901] INFO Server environment:host.name=10.68.191.161 (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,901] INFO Server environment:java.version=1.8.0_242 (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,901] INFO Server environment:java.vendor=Amazon.com Inc. (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,901] INFO Server environment:java.home=/Library/Java/JavaVirtualMachines/amazon-corretto-8.jdk/Contents/Home/jre (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,901] INFO Server environment:java.class.path=/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/activation-1.1.1.redhat-5.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/aopalliance-repackaged-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/argparse4j-0.7.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/audience-annotations-0.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/bcpkix-jdk15on-1.60.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/bcprov-jdk15on-1.60.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-cli-1.4.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-lang-2.6.0.redhat-7.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-lang3-3.9.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-api-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-basic-auth-extension-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-file-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-json-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-mirror-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-mirror-client-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-runtime-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-transforms-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-api-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-locator-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-utils-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-annotations-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-core-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-databind-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-dataformat-csv-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-datatype-jdk8-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-jaxrs-base-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-jaxrs-json-provider-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-jaxb-annotations-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-paranamer-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-scala_2.12-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.activation-api-1.2.1.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.annotation-api-1.3.4.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.inject-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.ws.rs-api-2.1.5.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.xml.bind-api-2.3.2.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javassist-3.22.0.GA-redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javax.servlet-api-3.1.0.redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javax.ws.rs-api-2.1.1.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jaxb-api-2.3.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-client-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-common-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-container-servlet-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-container-servlet-core-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-hk2-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-media-jaxb-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-server-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-client-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-continuation-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-http-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-io-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-security-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-server-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-servlet-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-servlets-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-util-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jmx_prometheus_javaagent-0.12.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jopt-simple-5.0.4.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/json-smart-1.1.1.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jsonevent-layout-1.7.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-clients-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-log4j-appender-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-client-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-common-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-keycloak-authorizer-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-server-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-examples-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-scala_2.12-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-test-utils-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-tools-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka_2.12-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/keycloak-common-7.0.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/keycloak-core-7.0.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/log4j-1.2.17.redhat-3.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/lz4-java-1.6.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/maven-artifact-3.6.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/metrics-core-2.2.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-buffer-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-codec-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-common-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-handler-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-resolver-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-native-epoll-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-native-unix-common-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-api-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-kafka-client-0.1.11.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-noop-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-util-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/osgi-resource-locator-1.0.3.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/paranamer-2.8.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/plexus-utils-3.2.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/reflections-0.9.12.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/rocksdbjni-5.18.3.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-collection-compat_2.12-2.1.2.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-java8-compat_2.12-0.9.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-library-2.12.10.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-logging_2.12-3.9.0.redhat-00008.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-reflect-2.12.10.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/slf4j-api-1.7.25.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/slf4j-log4j12-1.7.25.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/snappy-java-1.1.7.2-redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/validation-api-2.0.1.Final-redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zookeeper-3.5.7.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zookeeper-jute-3.5.7.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zstd-jni-1.4.3.1-redhat-00002.jar (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,902] INFO Server environment:java.library.path=/Users/kmurakat/Library/Java/Extensions:/Library/Java/Extensions:/Network/Library/Java/Extensions:/System/Library/Java/Extensions:/usr/lib/java:. (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,902] INFO Server environment:java.io.tmpdir=/var/folders/0f/5cgwwj_972n16fd0qd6jt3b80000gn/T/ (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,902] INFO Server environment:java.compiler=<NA> (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,902] INFO Server environment:os.name=Mac OS X (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,903] INFO Server environment:os.arch=x86_64 (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,903] INFO Server environment:os.version=10.15.1 (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,903] INFO Server environment:user.name=kmurakat (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,903] INFO Server environment:user.home=/Users/kmurakat (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,903] INFO Server environment:user.dir=/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005 (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,903] INFO Server environment:os.memory.free=497MB (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,903] INFO Server environment:os.memory.max=512MB (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,903] INFO Server environment:os.memory.total=512MB (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,904] INFO minSessionTimeout set to 6000 (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,904] INFO maxSessionTimeout set to 60000 (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,905] INFO Created server with tickTime 3000 minSessionTimeout 6000 maxSessionTimeout 60000 datadir /tmp/zookeeper/version-2 snapdir /tmp/zookeeper/version-2 (org.apache.zookeeper.server.ZooKeeperServer)
[2020-03-29 16:46:00,924] INFO Using org.apache.zookeeper.server.NIOServerCnxnFactory as server connection factory (org.apache.zookeeper.server.ServerCnxnFactory)
[2020-03-29 16:46:00,932] INFO Configuring NIO connection handler with 10s sessionless connection timeout, 2 selector thread(s), 16 worker threads, and 64 kB direct buffers. (org.apache.zookeeper.server.NIOServerCnxnFactory)
[2020-03-29 16:46:00,947] INFO binding to port 0.0.0.0/0.0.0.0:2181 (org.apache.zookeeper.server.NIOServerCnxnFactory)
[2020-03-29 16:46:00,964] INFO zookeeper.snapshotSizeFactor = 0.33 (org.apache.zookeeper.server.ZKDatabase)
[2020-03-29 16:46:00,968] INFO Snapshotting: 0x0 to /tmp/zookeeper/version-2/snapshot.0 (org.apache.zookeeper.server.persistence.FileTxnSnapLog)
[2020-03-29 16:46:00,971] INFO Snapshotting: 0x0 to /tmp/zookeeper/version-2/snapshot.0 (org.apache.zookeeper.server.persistence.FileTxnSnapLog)
[2020-03-29 16:46:00,987] INFO Using checkIntervalMs=60000 maxPerMinute=10000 (org.apache.zookeeper.server.ContainerManager)
```

4. 別コマンドプロンプトより、kakfaを起動する。

```
% cd /Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005
% bin/kafka-server-start.sh config/server.properties
[2020-03-29 16:47:33,491] INFO Registered kafka:type=kafka.Log4jController MBean (kafka.utils.Log4jControllerRegistration$)
[2020-03-29 16:47:33,972] INFO Registered signal handlers for TERM, INT, HUP (org.apache.kafka.common.utils.LoggingSignalHandler)
[2020-03-29 16:47:33,973] INFO starting (kafka.server.KafkaServer)
[2020-03-29 16:47:33,974] INFO Connecting to zookeeper on localhost:2181 (kafka.server.KafkaServer)
[2020-03-29 16:47:33,988] INFO [ZooKeeperClient Kafka server] Initializing a new session to localhost:2181. (kafka.zookeeper.ZooKeeperClient)
[2020-03-29 16:47:33,994] INFO Client environment:zookeeper.version=3.5.7-d01ffa89069093d4dd53c9748f2bddf8aee769cd, built on 02/18/2020 15:07 GMT (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,994] INFO Client environment:host.name=10.68.191.161 (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,994] INFO Client environment:java.version=1.8.0_242 (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,994] INFO Client environment:java.vendor=Amazon.com Inc. (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,994] INFO Client environment:java.home=/Library/Java/JavaVirtualMachines/amazon-corretto-8.jdk/Contents/Home/jre (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,994] INFO Client environment:java.class.path=/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/activation-1.1.1.redhat-5.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/aopalliance-repackaged-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/argparse4j-0.7.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/audience-annotations-0.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/bcpkix-jdk15on-1.60.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/bcprov-jdk15on-1.60.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-cli-1.4.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-lang-2.6.0.redhat-7.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-lang3-3.9.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-api-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-basic-auth-extension-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-file-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-json-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-mirror-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-mirror-client-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-runtime-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-transforms-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-api-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-locator-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-utils-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-annotations-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-core-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-databind-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-dataformat-csv-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-datatype-jdk8-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-jaxrs-base-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-jaxrs-json-provider-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-jaxb-annotations-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-paranamer-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-scala_2.12-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.activation-api-1.2.1.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.annotation-api-1.3.4.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.inject-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.ws.rs-api-2.1.5.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.xml.bind-api-2.3.2.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javassist-3.22.0.GA-redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javax.servlet-api-3.1.0.redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javax.ws.rs-api-2.1.1.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jaxb-api-2.3.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-client-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-common-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-container-servlet-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-container-servlet-core-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-hk2-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-media-jaxb-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-server-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-client-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-continuation-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-http-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-io-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-security-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-server-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-servlet-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-servlets-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-util-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jmx_prometheus_javaagent-0.12.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jopt-simple-5.0.4.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/json-smart-1.1.1.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jsonevent-layout-1.7.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-clients-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-log4j-appender-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-client-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-common-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-keycloak-authorizer-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-server-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-examples-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-scala_2.12-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-test-utils-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-tools-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka_2.12-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/keycloak-common-7.0.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/keycloak-core-7.0.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/log4j-1.2.17.redhat-3.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/lz4-java-1.6.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/maven-artifact-3.6.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/metrics-core-2.2.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-buffer-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-codec-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-common-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-handler-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-resolver-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-native-epoll-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-native-unix-common-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-api-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-kafka-client-0.1.11.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-noop-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-util-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/osgi-resource-locator-1.0.3.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/paranamer-2.8.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/plexus-utils-3.2.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/reflections-0.9.12.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/rocksdbjni-5.18.3.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-collection-compat_2.12-2.1.2.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-java8-compat_2.12-0.9.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-library-2.12.10.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-logging_2.12-3.9.0.redhat-00008.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-reflect-2.12.10.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/slf4j-api-1.7.25.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/slf4j-log4j12-1.7.25.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/snappy-java-1.1.7.2-redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/validation-api-2.0.1.Final-redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zookeeper-3.5.7.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zookeeper-jute-3.5.7.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zstd-jni-1.4.3.1-redhat-00002.jar (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:java.library.path=/Users/kmurakat/Library/Java/Extensions:/Library/Java/Extensions:/Network/Library/Java/Extensions:/System/Library/Java/Extensions:/usr/lib/java:. (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:java.io.tmpdir=/var/folders/0f/5cgwwj_972n16fd0qd6jt3b80000gn/T/ (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:java.compiler=<NA> (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:os.name=Mac OS X (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:os.arch=x86_64 (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:os.version=10.15.1 (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:user.name=kmurakat (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:user.home=/Users/kmurakat (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:user.dir=/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005 (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:os.memory.free=997MB (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:os.memory.max=1024MB (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,995] INFO Client environment:os.memory.total=1024MB (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:33,997] INFO Initiating client connection, connectString=localhost:2181 sessionTimeout=6000 watcher=kafka.zookeeper.ZooKeeperClient$ZooKeeperClientWatcher$@7fa98a66 (org.apache.zookeeper.ZooKeeper)
[2020-03-29 16:47:34,003] INFO Setting -D jdk.tls.rejectClientInitiatedRenegotiation=true to disable client-initiated TLS renegotiation (org.apache.zookeeper.common.X509Util)
[2020-03-29 16:47:34,009] INFO jute.maxbuffer value is 4194304 Bytes (org.apache.zookeeper.ClientCnxnSocket)
[2020-03-29 16:47:34,016] INFO zookeeper.request.timeout value is 0. feature enabled= (org.apache.zookeeper.ClientCnxn)
[2020-03-29 16:47:34,018] INFO [ZooKeeperClient Kafka server] Waiting until connected. (kafka.zookeeper.ZooKeeperClient)
[2020-03-29 16:47:34,020] INFO Opening socket connection to server localhost/0:0:0:0:0:0:0:1:2181. Will not attempt to authenticate using SASL (unknown error) (org.apache.zookeeper.ClientCnxn)
[2020-03-29 16:47:34,034] INFO Socket connection established, initiating session, client: /0:0:0:0:0:0:0:1:53248, server: localhost/0:0:0:0:0:0:0:1:2181 (org.apache.zookeeper.ClientCnxn)
[2020-03-29 16:47:34,054] INFO Session establishment complete on server localhost/0:0:0:0:0:0:0:1:2181, sessionid = 0x1000062047e0000, negotiated timeout = 6000 (org.apache.zookeeper.ClientCnxn)
[2020-03-29 16:47:34,057] INFO [ZooKeeperClient Kafka server] Connected. (kafka.zookeeper.ZooKeeperClient)
[2020-03-29 16:47:34,289] INFO Cluster ID = L21eiMqFS2aS--GO4ZPzfw (kafka.server.KafkaServer)
[2020-03-29 16:47:34,292] WARN No meta.properties file under dir /tmp/kafka-logs/meta.properties (kafka.server.BrokerMetadataCheckpoint)
[2020-03-29 16:47:34,342] INFO KafkaConfig values: 
	advertised.host.name = null
	advertised.listeners = null
	advertised.port = null
	alter.config.policy.class.name = null
	alter.log.dirs.replication.quota.window.num = 11
	alter.log.dirs.replication.quota.window.size.seconds = 1
	authorizer.class.name = 
	auto.create.topics.enable = true
	auto.leader.rebalance.enable = true
	background.threads = 10
	broker.id = 0
	broker.id.generation.enable = true
	broker.rack = null
	client.quota.callback.class = null
	compression.type = producer
	connection.failed.authentication.delay.ms = 100
	connections.max.idle.ms = 600000
	connections.max.reauth.ms = 0
	control.plane.listener.name = null
	controlled.shutdown.enable = true
	controlled.shutdown.max.retries = 3
	controlled.shutdown.retry.backoff.ms = 5000
	controller.socket.timeout.ms = 30000
	create.topic.policy.class.name = null
	default.replication.factor = 1
	delegation.token.expiry.check.interval.ms = 3600000
	delegation.token.expiry.time.ms = 86400000
	delegation.token.master.key = null
	delegation.token.max.lifetime.ms = 604800000
	delete.records.purgatory.purge.interval.requests = 1
	delete.topic.enable = true
	fetch.purgatory.purge.interval.requests = 1000
	group.initial.rebalance.delay.ms = 0
	group.max.session.timeout.ms = 1800000
	group.max.size = 2147483647
	group.min.session.timeout.ms = 6000
	host.name = 
	inter.broker.listener.name = null
	inter.broker.protocol.version = 2.4-IV1
	kafka.metrics.polling.interval.secs = 10
	kafka.metrics.reporters = []
	leader.imbalance.check.interval.seconds = 300
	leader.imbalance.per.broker.percentage = 10
	listener.security.protocol.map = PLAINTEXT:PLAINTEXT,SSL:SSL,SASL_PLAINTEXT:SASL_PLAINTEXT,SASL_SSL:SASL_SSL
	listeners = null
	log.cleaner.backoff.ms = 15000
	log.cleaner.dedupe.buffer.size = 134217728
	log.cleaner.delete.retention.ms = 86400000
	log.cleaner.enable = true
	log.cleaner.io.buffer.load.factor = 0.9
	log.cleaner.io.buffer.size = 524288
	log.cleaner.io.max.bytes.per.second = 1.7976931348623157E308
	log.cleaner.max.compaction.lag.ms = 9223372036854775807
	log.cleaner.min.cleanable.ratio = 0.5
	log.cleaner.min.compaction.lag.ms = 0
	log.cleaner.threads = 1
	log.cleanup.policy = [delete]
	log.dir = /tmp/kafka-logs
	log.dirs = /tmp/kafka-logs
	log.flush.interval.messages = 9223372036854775807
	log.flush.interval.ms = null
	log.flush.offset.checkpoint.interval.ms = 60000
	log.flush.scheduler.interval.ms = 9223372036854775807
	log.flush.start.offset.checkpoint.interval.ms = 60000
	log.index.interval.bytes = 4096
	log.index.size.max.bytes = 10485760
	log.message.downconversion.enable = true
	log.message.format.version = 2.4-IV1
	log.message.timestamp.difference.max.ms = 9223372036854775807
	log.message.timestamp.type = CreateTime
	log.preallocate = false
	log.retention.bytes = -1
	log.retention.check.interval.ms = 300000
	log.retention.hours = 168
	log.retention.minutes = null
	log.retention.ms = null
	log.roll.hours = 168
	log.roll.jitter.hours = 0
	log.roll.jitter.ms = null
	log.roll.ms = null
	log.segment.bytes = 1073741824
	log.segment.delete.delay.ms = 60000
	max.connections = 2147483647
	max.connections.per.ip = 2147483647
	max.connections.per.ip.overrides = 
	max.incremental.fetch.session.cache.slots = 1000
	message.max.bytes = 1000012
	metric.reporters = []
	metrics.num.samples = 2
	metrics.recording.level = INFO
	metrics.sample.window.ms = 30000
	min.insync.replicas = 1
	num.io.threads = 8
	num.network.threads = 3
	num.partitions = 1
	num.recovery.threads.per.data.dir = 1
	num.replica.alter.log.dirs.threads = null
	num.replica.fetchers = 1
	offset.metadata.max.bytes = 4096
	offsets.commit.required.acks = -1
	offsets.commit.timeout.ms = 5000
	offsets.load.buffer.size = 5242880
	offsets.retention.check.interval.ms = 600000
	offsets.retention.minutes = 10080
	offsets.topic.compression.codec = 0
	offsets.topic.num.partitions = 50
	offsets.topic.replication.factor = 1
	offsets.topic.segment.bytes = 104857600
	password.encoder.cipher.algorithm = AES/CBC/PKCS5Padding
	password.encoder.iterations = 4096
	password.encoder.key.length = 128
	password.encoder.keyfactory.algorithm = null
	password.encoder.old.secret = null
	password.encoder.secret = null
	port = 9092
	principal.builder.class = null
	producer.purgatory.purge.interval.requests = 1000
	queued.max.request.bytes = -1
	queued.max.requests = 500
	quota.consumer.default = 9223372036854775807
	quota.producer.default = 9223372036854775807
	quota.window.num = 11
	quota.window.size.seconds = 1
	replica.fetch.backoff.ms = 1000
	replica.fetch.max.bytes = 1048576
	replica.fetch.min.bytes = 1
	replica.fetch.response.max.bytes = 10485760
	replica.fetch.wait.max.ms = 500
	replica.high.watermark.checkpoint.interval.ms = 5000
	replica.lag.time.max.ms = 10000
	replica.selector.class = null
	replica.socket.receive.buffer.bytes = 65536
	replica.socket.timeout.ms = 30000
	replication.quota.window.num = 11
	replication.quota.window.size.seconds = 1
	request.timeout.ms = 30000
	reserved.broker.max.id = 1000
	sasl.client.callback.handler.class = null
	sasl.enabled.mechanisms = [GSSAPI]
	sasl.jaas.config = null
	sasl.kerberos.kinit.cmd = /usr/bin/kinit
	sasl.kerberos.min.time.before.relogin = 60000
	sasl.kerberos.principal.to.local.rules = [DEFAULT]
	sasl.kerberos.service.name = null
	sasl.kerberos.ticket.renew.jitter = 0.05
	sasl.kerberos.ticket.renew.window.factor = 0.8
	sasl.login.callback.handler.class = null
	sasl.login.class = null
	sasl.login.refresh.buffer.seconds = 300
	sasl.login.refresh.min.period.seconds = 60
	sasl.login.refresh.window.factor = 0.8
	sasl.login.refresh.window.jitter = 0.05
	sasl.mechanism.inter.broker.protocol = GSSAPI
	sasl.server.callback.handler.class = null
	security.inter.broker.protocol = PLAINTEXT
	security.providers = null
	socket.receive.buffer.bytes = 102400
	socket.request.max.bytes = 104857600
	socket.send.buffer.bytes = 102400
	ssl.cipher.suites = []
	ssl.client.auth = none
	ssl.enabled.protocols = [TLSv1.2, TLSv1.1, TLSv1]
	ssl.endpoint.identification.algorithm = https
	ssl.key.password = null
	ssl.keymanager.algorithm = SunX509
	ssl.keystore.location = null
	ssl.keystore.password = null
	ssl.keystore.type = JKS
	ssl.principal.mapping.rules = DEFAULT
	ssl.protocol = TLS
	ssl.provider = null
	ssl.secure.random.implementation = null
	ssl.trustmanager.algorithm = PKIX
	ssl.truststore.location = null
	ssl.truststore.password = null
	ssl.truststore.type = JKS
	transaction.abort.timed.out.transaction.cleanup.interval.ms = 60000
	transaction.max.timeout.ms = 900000
	transaction.remove.expired.transaction.cleanup.interval.ms = 3600000
	transaction.state.log.load.buffer.size = 5242880
	transaction.state.log.min.isr = 1
	transaction.state.log.num.partitions = 50
	transaction.state.log.replication.factor = 1
	transaction.state.log.segment.bytes = 104857600
	transactional.id.expiration.ms = 604800000
	unclean.leader.election.enable = false
	zookeeper.connect = localhost:2181
	zookeeper.connection.timeout.ms = 6000
	zookeeper.max.in.flight.requests = 10
	zookeeper.session.timeout.ms = 6000
	zookeeper.set.acl = false
	zookeeper.sync.time.ms = 2000
 (kafka.server.KafkaConfig)
[2020-03-29 16:47:34,351] INFO KafkaConfig values: 
	advertised.host.name = null
	advertised.listeners = null
	advertised.port = null
	alter.config.policy.class.name = null
	alter.log.dirs.replication.quota.window.num = 11
	alter.log.dirs.replication.quota.window.size.seconds = 1
	authorizer.class.name = 
	auto.create.topics.enable = true
	auto.leader.rebalance.enable = true
	background.threads = 10
	broker.id = 0
	broker.id.generation.enable = true
	broker.rack = null
	client.quota.callback.class = null
	compression.type = producer
	connection.failed.authentication.delay.ms = 100
	connections.max.idle.ms = 600000
	connections.max.reauth.ms = 0
	control.plane.listener.name = null
	controlled.shutdown.enable = true
	controlled.shutdown.max.retries = 3
	controlled.shutdown.retry.backoff.ms = 5000
	controller.socket.timeout.ms = 30000
	create.topic.policy.class.name = null
	default.replication.factor = 1
	delegation.token.expiry.check.interval.ms = 3600000
	delegation.token.expiry.time.ms = 86400000
	delegation.token.master.key = null
	delegation.token.max.lifetime.ms = 604800000
	delete.records.purgatory.purge.interval.requests = 1
	delete.topic.enable = true
	fetch.purgatory.purge.interval.requests = 1000
	group.initial.rebalance.delay.ms = 0
	group.max.session.timeout.ms = 1800000
	group.max.size = 2147483647
	group.min.session.timeout.ms = 6000
	host.name = 
	inter.broker.listener.name = null
	inter.broker.protocol.version = 2.4-IV1
	kafka.metrics.polling.interval.secs = 10
	kafka.metrics.reporters = []
	leader.imbalance.check.interval.seconds = 300
	leader.imbalance.per.broker.percentage = 10
	listener.security.protocol.map = PLAINTEXT:PLAINTEXT,SSL:SSL,SASL_PLAINTEXT:SASL_PLAINTEXT,SASL_SSL:SASL_SSL
	listeners = null
	log.cleaner.backoff.ms = 15000
	log.cleaner.dedupe.buffer.size = 134217728
	log.cleaner.delete.retention.ms = 86400000
	log.cleaner.enable = true
	log.cleaner.io.buffer.load.factor = 0.9
	log.cleaner.io.buffer.size = 524288
	log.cleaner.io.max.bytes.per.second = 1.7976931348623157E308
	log.cleaner.max.compaction.lag.ms = 9223372036854775807
	log.cleaner.min.cleanable.ratio = 0.5
	log.cleaner.min.compaction.lag.ms = 0
	log.cleaner.threads = 1
	log.cleanup.policy = [delete]
	log.dir = /tmp/kafka-logs
	log.dirs = /tmp/kafka-logs
	log.flush.interval.messages = 9223372036854775807
	log.flush.interval.ms = null
	log.flush.offset.checkpoint.interval.ms = 60000
	log.flush.scheduler.interval.ms = 9223372036854775807
	log.flush.start.offset.checkpoint.interval.ms = 60000
	log.index.interval.bytes = 4096
	log.index.size.max.bytes = 10485760
	log.message.downconversion.enable = true
	log.message.format.version = 2.4-IV1
	log.message.timestamp.difference.max.ms = 9223372036854775807
	log.message.timestamp.type = CreateTime
	log.preallocate = false
	log.retention.bytes = -1
	log.retention.check.interval.ms = 300000
	log.retention.hours = 168
	log.retention.minutes = null
	log.retention.ms = null
	log.roll.hours = 168
	log.roll.jitter.hours = 0
	log.roll.jitter.ms = null
	log.roll.ms = null
	log.segment.bytes = 1073741824
	log.segment.delete.delay.ms = 60000
	max.connections = 2147483647
	max.connections.per.ip = 2147483647
	max.connections.per.ip.overrides = 
	max.incremental.fetch.session.cache.slots = 1000
	message.max.bytes = 1000012
	metric.reporters = []
	metrics.num.samples = 2
	metrics.recording.level = INFO
	metrics.sample.window.ms = 30000
	min.insync.replicas = 1
	num.io.threads = 8
	num.network.threads = 3
	num.partitions = 1
	num.recovery.threads.per.data.dir = 1
	num.replica.alter.log.dirs.threads = null
	num.replica.fetchers = 1
	offset.metadata.max.bytes = 4096
	offsets.commit.required.acks = -1
	offsets.commit.timeout.ms = 5000
	offsets.load.buffer.size = 5242880
	offsets.retention.check.interval.ms = 600000
	offsets.retention.minutes = 10080
	offsets.topic.compression.codec = 0
	offsets.topic.num.partitions = 50
	offsets.topic.replication.factor = 1
	offsets.topic.segment.bytes = 104857600
	password.encoder.cipher.algorithm = AES/CBC/PKCS5Padding
	password.encoder.iterations = 4096
	password.encoder.key.length = 128
	password.encoder.keyfactory.algorithm = null
	password.encoder.old.secret = null
	password.encoder.secret = null
	port = 9092
	principal.builder.class = null
	producer.purgatory.purge.interval.requests = 1000
	queued.max.request.bytes = -1
	queued.max.requests = 500
	quota.consumer.default = 9223372036854775807
	quota.producer.default = 9223372036854775807
	quota.window.num = 11
	quota.window.size.seconds = 1
	replica.fetch.backoff.ms = 1000
	replica.fetch.max.bytes = 1048576
	replica.fetch.min.bytes = 1
	replica.fetch.response.max.bytes = 10485760
	replica.fetch.wait.max.ms = 500
	replica.high.watermark.checkpoint.interval.ms = 5000
	replica.lag.time.max.ms = 10000
	replica.selector.class = null
	replica.socket.receive.buffer.bytes = 65536
	replica.socket.timeout.ms = 30000
	replication.quota.window.num = 11
	replication.quota.window.size.seconds = 1
	request.timeout.ms = 30000
	reserved.broker.max.id = 1000
	sasl.client.callback.handler.class = null
	sasl.enabled.mechanisms = [GSSAPI]
	sasl.jaas.config = null
	sasl.kerberos.kinit.cmd = /usr/bin/kinit
	sasl.kerberos.min.time.before.relogin = 60000
	sasl.kerberos.principal.to.local.rules = [DEFAULT]
	sasl.kerberos.service.name = null
	sasl.kerberos.ticket.renew.jitter = 0.05
	sasl.kerberos.ticket.renew.window.factor = 0.8
	sasl.login.callback.handler.class = null
	sasl.login.class = null
	sasl.login.refresh.buffer.seconds = 300
	sasl.login.refresh.min.period.seconds = 60
	sasl.login.refresh.window.factor = 0.8
	sasl.login.refresh.window.jitter = 0.05
	sasl.mechanism.inter.broker.protocol = GSSAPI
	sasl.server.callback.handler.class = null
	security.inter.broker.protocol = PLAINTEXT
	security.providers = null
	socket.receive.buffer.bytes = 102400
	socket.request.max.bytes = 104857600
	socket.send.buffer.bytes = 102400
	ssl.cipher.suites = []
	ssl.client.auth = none
	ssl.enabled.protocols = [TLSv1.2, TLSv1.1, TLSv1]
	ssl.endpoint.identification.algorithm = https
	ssl.key.password = null
	ssl.keymanager.algorithm = SunX509
	ssl.keystore.location = null
	ssl.keystore.password = null
	ssl.keystore.type = JKS
	ssl.principal.mapping.rules = DEFAULT
	ssl.protocol = TLS
	ssl.provider = null
	ssl.secure.random.implementation = null
	ssl.trustmanager.algorithm = PKIX
	ssl.truststore.location = null
	ssl.truststore.password = null
	ssl.truststore.type = JKS
	transaction.abort.timed.out.transaction.cleanup.interval.ms = 60000
	transaction.max.timeout.ms = 900000
	transaction.remove.expired.transaction.cleanup.interval.ms = 3600000
	transaction.state.log.load.buffer.size = 5242880
	transaction.state.log.min.isr = 1
	transaction.state.log.num.partitions = 50
	transaction.state.log.replication.factor = 1
	transaction.state.log.segment.bytes = 104857600
	transactional.id.expiration.ms = 604800000
	unclean.leader.election.enable = false
	zookeeper.connect = localhost:2181
	zookeeper.connection.timeout.ms = 6000
	zookeeper.max.in.flight.requests = 10
	zookeeper.session.timeout.ms = 6000
	zookeeper.set.acl = false
	zookeeper.sync.time.ms = 2000
 (kafka.server.KafkaConfig)
[2020-03-29 16:47:34,374] INFO [ThrottledChannelReaper-Fetch]: Starting (kafka.server.ClientQuotaManager$ThrottledChannelReaper)
[2020-03-29 16:47:34,374] INFO [ThrottledChannelReaper-Produce]: Starting (kafka.server.ClientQuotaManager$ThrottledChannelReaper)
[2020-03-29 16:47:34,375] INFO [ThrottledChannelReaper-Request]: Starting (kafka.server.ClientQuotaManager$ThrottledChannelReaper)
[2020-03-29 16:47:34,395] INFO Log directory /tmp/kafka-logs not found, creating it. (kafka.log.LogManager)
[2020-03-29 16:47:34,403] INFO Loading logs. (kafka.log.LogManager)
[2020-03-29 16:47:34,410] INFO Logs loading complete in 7 ms. (kafka.log.LogManager)
[2020-03-29 16:47:34,423] INFO Starting log cleanup with a period of 300000 ms. (kafka.log.LogManager)
[2020-03-29 16:47:34,426] INFO Starting log flusher with a default period of 9223372036854775807 ms. (kafka.log.LogManager)
[2020-03-29 16:47:34,742] INFO Awaiting socket connections on 0.0.0.0:9092. (kafka.network.Acceptor)
[2020-03-29 16:47:34,765] INFO [SocketServer brokerId=0] Created data-plane acceptor and processors for endpoint : EndPoint(null,9092,ListenerName(PLAINTEXT),PLAINTEXT) (kafka.network.SocketServer)
[2020-03-29 16:47:34,766] INFO [SocketServer brokerId=0] Started 1 acceptor threads for data-plane (kafka.network.SocketServer)
[2020-03-29 16:47:34,783] INFO [ExpirationReaper-0-Produce]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2020-03-29 16:47:34,784] INFO [ExpirationReaper-0-Fetch]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2020-03-29 16:47:34,785] INFO [ExpirationReaper-0-DeleteRecords]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2020-03-29 16:47:34,785] INFO [ExpirationReaper-0-ElectLeader]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2020-03-29 16:47:34,796] INFO [LogDirFailureHandler]: Starting (kafka.server.ReplicaManager$LogDirFailureHandler)
[2020-03-29 16:47:34,814] INFO Creating /brokers/ids/0 (is it secure? false) (kafka.zk.KafkaZkClient)
[2020-03-29 16:47:34,833] INFO Stat of the created znode at /brokers/ids/0 is: 24,24,1585468054825,1585468054825,1,0,0,72058015020089344,196,0,24
 (kafka.zk.KafkaZkClient)
[2020-03-29 16:47:34,833] INFO Registered broker 0 at path /brokers/ids/0 with addresses: ArrayBuffer(EndPoint(10.68.191.161,9092,ListenerName(PLAINTEXT),PLAINTEXT)), czxid (broker epoch): 24 (kafka.zk.KafkaZkClient)
[2020-03-29 16:47:34,880] INFO [ExpirationReaper-0-topic]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2020-03-29 16:47:34,883] INFO [ExpirationReaper-0-Heartbeat]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2020-03-29 16:47:34,883] INFO [ExpirationReaper-0-Rebalance]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2020-03-29 16:47:34,893] INFO Successfully created /controller_epoch with initial epoch 0 (kafka.zk.KafkaZkClient)
[2020-03-29 16:47:34,910] INFO [GroupCoordinator 0]: Starting up. (kafka.coordinator.group.GroupCoordinator)
[2020-03-29 16:47:34,911] INFO [GroupCoordinator 0]: Startup complete. (kafka.coordinator.group.GroupCoordinator)
[2020-03-29 16:47:34,914] INFO [GroupMetadataManager brokerId=0] Removed 0 expired offsets in 3 milliseconds. (kafka.coordinator.group.GroupMetadataManager)
[2020-03-29 16:47:34,921] INFO [ProducerId Manager 0]: Acquired new producerId block (brokerId:0,blockStartProducerId:0,blockEndProducerId:999) by writing to Zk with path version 1 (kafka.coordinator.transaction.ProducerIdManager)
[2020-03-29 16:47:34,939] INFO [TransactionCoordinator id=0] Starting up. (kafka.coordinator.transaction.TransactionCoordinator)
[2020-03-29 16:47:34,940] INFO [Transaction Marker Channel Manager 0]: Starting (kafka.coordinator.transaction.TransactionMarkerChannelManager)
[2020-03-29 16:47:34,940] INFO [TransactionCoordinator id=0] Startup complete. (kafka.coordinator.transaction.TransactionCoordinator)
[2020-03-29 16:47:34,964] INFO [ExpirationReaper-0-AlterAcls]: Starting (kafka.server.DelayedOperationPurgatory$ExpiredOperationReaper)
[2020-03-29 16:47:34,993] INFO [/config/changes-event-process-thread]: Starting (kafka.common.ZkNodeChangeNotificationListener$ChangeEventProcessThread)
[2020-03-29 16:47:35,007] INFO [SocketServer brokerId=0] Started data-plane processors for 1 acceptors (kafka.network.SocketServer)
[2020-03-29 16:47:35,010] INFO Kafka version: 2.4.0.redhat-00005 (org.apache.kafka.common.utils.AppInfoParser)
[2020-03-29 16:47:35,011] INFO Kafka commitId: bc61f1c575849a1e (org.apache.kafka.common.utils.AppInfoParser)
[2020-03-29 16:47:35,011] INFO Kafka startTimeMs: 1585468055008 (org.apache.kafka.common.utils.AppInfoParser)
[2020-03-29 16:47:35,012] INFO [KafkaServer id=0] started (kafka.server.KafkaServer)
```

5. 別コマンドプロンプトで単一のパーティションと1つのレプリカのみを持つ「test」という名前のトピックを作成する。

```
% cd /Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005
% bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test
```

6. 作成したトピックを確認する。
```
% bin/kafka-topics.sh --list --bootstrap-server localhost:9092
test
```

7. プロデューサーを実行し、コンソールにいくつかのメッセージを入力してKafkaサーバーに送信します。
※Topicを作成したコマンドプロンプト

```
% bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
>first hoge
>first foo
>first bar
```

8. コンシューマを実行し、プロデューサーが送信したメッセージを受信し、標準出力へ出力する。
※別プロンプトで実行

```
% cd /Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005
% bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
first hoge
first foo
first bar
```

以上

■マルチブローカーを使用したメッセージの送受信

1. ブローカー毎の設定ファイルを作成する。
※先程使用したプロデューサーもしくはコンシュマーのコマンドプロンプトを使用する。
※zookeeperとkafkaのプロンプトはそのままにして、プロセスが起動している状態とする。

```
% cp config/server.properties config/server-1.properties
% cp config/server.properties config/server-2.properties
```

2. 同一PCで複数のブローカーを起動するため、ノードやポート、ログディレクトリが重複しないように編集する。

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

3. 別プロンプトで上記編集したサーバープロセスを起動し、計3つのKafkaサーバーを起動する。

```
% bin/kafka-server-start.sh config/server-1.properties &
% bin/kafka-server-start.sh config/server-2.properties &
```


4. 複数係数[replication-factor]が3の新しいトピックを作成する。

```
% bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 3 --partitions 1 --topic my-replicated-topic
```

5. 作成したトピックを確認する。

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

6. 新しく作成したトピックにメッセージを送信[publish]する。

```
% bin/kafka-console-producer.sh --broker-list localhost:9092 --topic my-replicated-topic
>second hoge
>second foo
>second bar
```

7. メッセージを受信する。

```
% bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --from-beginning --topic my-replicated-topic
second hoge
second foo
second bar
```

8. フォールトトレランスをテストする。ブローカー2がリーダーとして機能していたので、プロセスを殺す。

```
% ps aux | grep server-2.properties
kmurakat          9576   0.0  0.0  4277512    688 s002  R+    5:26PM   0:00.01 grep server-2.properties
kmurakat          7511   0.0  2.4  7009320 395348 s003  SN    5:12PM   0:19.79 /usr/bin/java -Xmx1G -Xms1G -server -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:InitiatingHeapOccupancyPercent=35 -XX:+ExplicitGCInvokesConcurrent -Djava.awt.headless=true -Xloggc:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../logs/kafkaServer-gc.log -verbose:gc -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintGCTimeStamps -XX:+UseGCLogFileRotation -XX:NumberOfGCLogFiles=10 -XX:GCLogFileSize=100M -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Dkafka.logs.dir=/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../logs -Dlog4j.configuration=file:bin/../config/log4j.properties -cp /Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/activation-1.1.1.redhat-5.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/aopalliance-repackaged-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/argparse4j-0.7.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/audience-annotations-0.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/bcpkix-jdk15on-1.60.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/bcprov-jdk15on-1.60.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-cli-1.4.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-lang-2.6.0.redhat-7.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/commons-lang3-3.9.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-api-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-basic-auth-extension-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-file-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-json-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-mirror-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-mirror-client-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-runtime-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/connect-transforms-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-api-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-locator-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/hk2-utils-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-annotations-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-core-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-databind-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-dataformat-csv-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-datatype-jdk8-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-jaxrs-base-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-jaxrs-json-provider-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-jaxb-annotations-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-paranamer-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jackson-module-scala_2.12-2.10.2.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.activation-api-1.2.1.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.annotation-api-1.3.4.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.inject-2.5.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.ws.rs-api-2.1.5.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jakarta.xml.bind-api-2.3.2.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javassist-3.22.0.GA-redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javax.servlet-api-3.1.0.redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/javax.ws.rs-api-2.1.1.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jaxb-api-2.3.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-client-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-common-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-container-servlet-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-container-servlet-core-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-hk2-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-media-jaxb-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jersey-server-2.28.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-client-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-continuation-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-http-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-io-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-security-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-server-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-servlet-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-servlets-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jetty-util-9.4.26.v20200117-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jmx_prometheus_javaagent-0.12.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jopt-simple-5.0.4.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/json-smart-1.1.1.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/jsonevent-layout-1.7.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-clients-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-log4j-appender-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-client-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-common-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-keycloak-authorizer-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-oauth-server-0.3.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-examples-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-scala_2.12-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-streams-test-utils-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka-tools-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/kafka_2.12-2.4.0.redhat-00005.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/keycloak-common-7.0.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/keycloak-core-7.0.0.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/log4j-1.2.17.redhat-3.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/lz4-java-1.6.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/maven-artifact-3.6.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/metrics-core-2.2.0.redhat-00003.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-buffer-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-codec-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-common-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-handler-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-resolver-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-native-epoll-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/netty-transport-native-unix-common-4.1.45.Final-redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-api-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-kafka-client-0.1.11.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-noop-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/opentracing-util-0.33.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/osgi-resource-locator-1.0.3.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/paranamer-2.8.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/plexus-utils-3.2.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/reflections-0.9.12.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/rocksdbjni-5.18.3.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-collection-compat_2.12-2.1.2.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-java8-compat_2.12-0.9.0.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-library-2.12.10.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-logging_2.12-3.9.0.redhat-00008.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/scala-reflect-2.12.10.redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/slf4j-api-1.7.25.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/slf4j-log4j12-1.7.25.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/snappy-java-1.1.7.2-redhat-00002.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/validation-api-2.0.1.Final-redhat-1.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zookeeper-3.5.7.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zookeeper-jute-3.5.7.redhat-00001.jar:/Users/kmurakat/mylabs/kafka_2.12-2.4.0.redhat-00005/bin/../libs/zstd-jni-1.4.3.1-redhat-00002.jar kafka.Kafka config/server-2.properties
% kill -9 7511
% ps aux | grep server-2.properties
kmurakat          9641   0.0  0.0  4271368    688 s002  R+    5:29PM   0:00.01 grep server-2.properties
```

9. リーダーがフォロワーの1人に切り替わり、ノード2は同期レプリカセットに存在しなくなった。
```
% bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic my-replicated-topic
Topic: my-replicated-topic	PartitionCount: 1	ReplicationFactor: 3	Configs: segment.bytes=1073741824
	Topic: my-replicated-topic	Partition: 0	Leader: 1	Replicas: 2,1,0	Isr: 1,0
kmurakat@kmurakat-mac kafka_2.12-2.4.0.redhat-00005 % 
```

10. メッセージを送信する。※元のリーダーがダウンしてもメッセージは送信出来る。
```
% bin/kafka-console-producer.sh --broker-list localhost:9092 --topic my-replicated-topic
>thrid hoge
>third foo
>third bar
```

11. メッセージを受信する。※元のリーダーがダウンしてもメッセージは受信出来る。
```
% bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --from-beginning --topic my-replicated-topic
thrid hoge
third foo
third bar
```

