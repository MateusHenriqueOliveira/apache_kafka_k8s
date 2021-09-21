# kafka version = 2.8 [latest]

# https://www.confluent.io/hub/confluentinc/kafka-connect-jdbc
# https://www.confluent.io/hub/debezium/debezium-connector-sqlserver
# https://github.com/yousufdev/kafka-connect-append-schema
# https://mvnrepository.com/artifact/org.apache.kafka/connect-runtime/2.6.0

# get image from strimzi repository
# https://quay.io/repository/strimzi/kafka
FROM quay.io/strimzi/kafka:latest-kafka-2.8.0

# using root user
USER root:root

# create dirs

RUN mkdir -p /opt/kafka/plugins/kafka-connect-jdbc
RUN mkdir -p /opt/kafka/plugins/debezium-sqlserver-cdc
RUN mkdir -p /opt/kafka/plugins/kafka-connect-s3
RUN mkdir -p /opt/kafka/plugins/debezium-mongodb-cdc
RUN mkdir -p /opt/kafka/plugins/debezium-mysql-cdc
RUN mkdir -p /opt/kafka/plugins/debezium-postgres-cdc


# copy jar files

COPY ./jars/kafka-connect-jdbc/ /opt/kafka/plugins/kafka-connect-jdbc/
COPY ./jars/debezium-sqlserver-cdc/ /opt/kafka/plugins/debezium-sqlserver-cdc/
COPY ./jars/kafka-connect-s3/ /opt/kafka/plugins/kafka-connect-s3/
COPY ./jars/debezium-mongodb-cdc/ /opt/kafka/plugins/debezium-mongodb-cdc/
COPY ./jars/debezium-mysql-cdc/ /opt/kafka/plugins/debezium-mysql-cdc/
COPY ./jars/debezium-postgres-cdc/ /opt/kafka/plugins/debezium-postgres-cdc/


# user
USER 1001
