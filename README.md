# Jathena
### An Open Source Amazon Athena Proof of Concept


#### Parts

* Apache Drill
* Apache Zookeeper
* Minio
* Kubernetes

#### Installation 


**Prereqs:**

[Kubernetes](https://kubernetes.io)

[Helm](https://helm.sh)



#### Ordered Installation 

Install Minio

```bash
helm init // wait for helm to till

helm install stable/minio
```

Install Zookeeper 

```bash
kubectl create -f zookeeper.yaml
```

Install Apache Drill 

```bash
kubectl create -f drill.yaml
```

#### Final Steps

Add the Parquet file to Minio

You can do this via the RESTful API, but the UI is good enough. Bind the Minio port to your localhost and add the file:






Open Apache Drill


Query the file 
