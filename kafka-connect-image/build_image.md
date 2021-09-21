# Docker Build Kafka Connect Image for Strimzi
> building a new image to add the extra connectors and drivers to ingest data from different sources to kafka

https://hub.docker.com/r/strimzi/kafka

### build image and deploy hub
```sh
# pull latest image version
docker pull quay.io/strimzi/kafka:latest-kafka-2.8.0

# verify local images
docker images
strimzi/kafka

# build image
docker build . -t kafka-connect-strimzi:2.8

# access image
docker run -i -t  kafka-connect-strimzi:2.8 /bin/bash
/opt/kafka/plugins/
/opt/kafka/libs/

# docker hub [repositories]
https://hub.docker.com/repositories

# tag image
docker tag kafka-connect-strimzi:2.8 mateushenrique/kafka-connect-strimzi:2.8.1

# push image to registry
docker push mateushenrique/kafka-connect-strimzi:2.8.1

# remove old entries
docker rmi $(docker images --filter "dangling=true" -q --no-trunc) -f
```

### quick build
```sh
# build image faster
docker build . -t kafka-connect-strimzi:2.8
docker tag kafka-connect-strimzi:2.8 mateushenrique/kafka-connect-strimzi:2.8.1
docker push mateushenrique/kafka-connect-strimzi:2.8.1
```
