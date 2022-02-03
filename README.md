# java kafka docker demo

## run docker
    docker-compose up -d
    
## explore kafka
    docker exec -it kafka-broker bash
    ls /opt/bitnami/kafka/config
    ls /opt/bitnami/kafka/logs
    ls /opt/bitnami/kafka/bin

## create topic
    ./kafka-topics.sh \
            --create \
            --topic kafka.learning.tweets \
            --partitions 1 \
            --replication-factor 1 \
            --zookeeper zookeeper:2181

    ./kafka-topics.sh \
        --zookeeper zookeeper:2181 \
        --create \
        --topic kafka.learning.alerts \
        --partitions 1 \
        --replication-factor 1

    ./kafka-topics.sh \
            --zookeeper zookeeper:2181 \
            --list

## Getting details about a Topic

        ./kafka-topics.sh \
            --zookeeper zookeeper:2181 \
            --describe


## Publishing Messages to Topics

        ./kafka-console-producer.sh \
            --broker-list kafka:9092 \
            --topic kafka.learning.tweets

## Consuming Messages from Topics

        ./kafka-console-consumer.sh \
            --bootstrap-server kafka:9092 \
            --topic kafka.learning.tweets \
            --from-beginning

## Deleting Topics

        ./kafka-topics.sh \
            --zookeeper zookeeper:2181 \
            --delete \
            --topic kafka.learning.alerts






