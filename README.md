# kafka_cluster

- Create topic

  docker run --rm --net=kafka_cluster_default wurstmeister/kafka kafka-topics.sh --create --topic topic1 --replication-factor 3 --partitions 1 --bootstrap-server kafka1:9092,kafka2:9092,kafka3:9092

- Attach Publisher

  docker run --rm --net=kafka_cluster_default -it wurstmeister/kafka kafka-console-producer.sh --topic topic1 --bootstrap-server kafka1:9092,kafka2:9092,kafka3:9092

- Attach Subscriber

  docker run --rm --net=kafka_cluster_default wurstmeister/kafka kafka-console-consumer.sh --topic topic1 --from-beginning --bootstrap-server kafka1:9092,kafka2:9092,kafka3:9092

- Get information for topic in KAFKA

  docker run --rm --net=kafka_cluster_default wurstmeister/kafka kafka-topics.sh --bootstrap-server kafka1:9092,kafka2:9092,kafka3:9092 --describe --topic topic1

- Get all broker ids

  docker run --rm --net=kafka_cluster_default wurstmeister/kafka zookeeper-shell.sh zookeeper1:2181 ls /brokers/ids

- To find broker Id for container, use `docker-compose logs | grep brokerId` and manually check through to find.
