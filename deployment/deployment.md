### Deployment of Apache Kafka on Kubernetes

Few thicks to install in Apache Kafka 2.8 using Strimzi on k8s

Create namespaces
```sh
kubectl create namespace ingestion
kubectl create namespace processing
```


##### Install strimzi operator in this case we are using minikube with strimzi version 0.24

```sh
helm install kafka strimzi/strimzi-kafka-operator --namespace ingestion --version 0.25.0
```

In case of using minikube run the command line below in another bash session

```sh
minikube tunnel
```
This command create a loadbalancer for the single broker

##### Install Apache Kafka components

```sh
# broker and zookeeper version 2.8
kubectl apply -f yamls/ingestion/broker/kafka-ephemeral.yaml -n ingestion
kubectl apply -f yamls/ingestion/broker/kafka-jbod.yaml -n ingestion

# kafka connect
kubectl apply -f yamls/ingestion/kafka-connect/kafka-connect.yaml -n ingestion

# schema registry
helm install schema-registry helm-charts/cp-schema-registry --namespace ingestion

# processing - ksqldb
kubectl apply -f yamls/processing/ksqldb/ -n processing

# cruise Control
kubectl apply -f yamls/ingestion/cruise-control/kafka-rebalance.yaml -n ingestion

```

##### Kubernetes Cheat codes
```sh
# alias to use k as kubectl
alias k=kubectl

# list pods in ingestion namespaces
k get pods -n ingestion

# access log of a pod
$pod=?
k logs $pod -f


```
