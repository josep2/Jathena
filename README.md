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


#### Ordered Installation 

Install Minio

```
Run these three commands (Thanks: https://github.com/kubernetes/examples/blob/master/staging/storage/minio/README.md)
kubectl create -f https://github.com/kubernetes/kubernetes/blob/master/examples/storage/minio/minio-distributed-headless-service.yaml?raw=true
kubectl create -f https://github.com/kubernetes/kubernetes/blob/master/examples/storage/minio/minio-distributed-statefulset.yaml?raw=true
kubectl create -f https://github.com/kubernetes/kubernetes/blob/master/examples/storage/minio/minio-distributed-service.yaml?raw=true
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

1. Add the my-data.csv file to Minio
2. Edit and enable s3 in Apache Drill Admin Console
3. Query File 




#### Bonus

You can get the JDBC or ODBC connection for Drill by following the intrusctions [here](https://drill.apache.org/docs/using-the-jdbc-driver/). 
