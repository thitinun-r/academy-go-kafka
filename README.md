# academy-go-kafka
academy go kafka 


broker
consumer
topic
partition


Message
    - Timestamp
    - HeaderSet
    - Partionnumber
    - Offset
    - Key
    - value
      - MAX value size 1M


./bin/zookeeper-server-start.sh ./config/zookeeper.properties

./bin/kafka-server-start.sh ./config/server.properties

-- list topic 
bin/kafka-topics.sh --bootstrap-server localhost:9092 --list
bin/kafka-topics.sh --bootstrap-server localhost:9092 --list --exclude-internal

-- create topic
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --topic kafka-for-dev-topic --partitions 10

-- delete topic
bin/kafka-topics.sh --delete --bootstrap-server localhost:9092 --topic kafka-for-dev-topic


./bin/zookeeper-shell.sh localhost:2181

-- produce message
bin/kafka-console-producer.sh --topic <topic-name> --bootstrap-server <kafka-server>
bin/kafka-console-producer.sh --topic kafka-for-dev-topic --bootstrap-server localhost:9092
bin/kafka-console-producer.sh --topic kafka-for-dev-topic --bootstrap-server localhost:9092 --property "parse.key=true" --property "key.separator=:"



-- consumer message
bin/kafka-console-consumer.sh --topic <topic-name> --bootstrap-server <kafka-server> --from-beginning --property  print.key=true --group test-kafka

bin/kafka-console-consumer.sh --topic kafka-for-dev-topic --bootstrap-server localhost:9092 --from-beginning --property  print.key=true --group test-kafka



## config
    ### server
    log.dirs 
    num.partitions
    offsets.topic.replication.factor ควรมากกว่า 3  หรือเท่ากับ brokers
    log.retention.hours เก็บ log กี่ชัวโมง
    log.segment.bytes ขนาดของ  file log 
    log.retention.check.interval.ms  รอบการ check retention

    zookeeper.connect  ip zookeeper
    zookeeper.connection.timeout.ms  zookeeper connection timeout

    ### zookeeper
    dataDir
    clientPort