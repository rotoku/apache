# Apache Kafka
Apache Kafka é uma plataforma open-source de processamento de streams desenvolvida pela Apache Software Foundation, escrita em Scala e Java. O projeto tem como objetivo fornecer uma plataforma unificada, de alta capacidade e baixa latência para tratamento de dados em tempo real. 

## Enter home dir
```
cd ${KAFKA_HOME}
```

## Start ZooKeeper
```
bin/zookeeper-server-start.sh config/zookeeper.properties &
```

## find some attributes into properties files
```
grep "broker.id=" ${KAFKA_HOME}/config/server-*.properties
grep "listeners=" ${KAFKA_HOME}/config/server-*.properties
grep "log.dirs=" ${KAFKA_HOME}/config/server-*.properties
```

## Start Kafka Server
```
bin/kafka-server-start.sh config/server-0.properties &
bin/kafka-server-start.sh config/server-1.properties &
bin/kafka-server-start.sh config/server-2.properties &
```

## Create topic, replication-factor: fator de replicação para ser espalhadas em vários brokers provendo tolerância a falhas, partitions: número de partições para armazenar os topics
```
bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 3 --partitions 3 --topic my-replicated-topic
```