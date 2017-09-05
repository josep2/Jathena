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
kubectl create -f https://github.com/kubernetes/kubernetes/blob/master/examples/storage/minio/minio-standalone-pvc.yaml?raw=true
kubectl create -f https://github.com/kubernetes/kubernetes/blob/master/examples/storage/minio/minio-standalone-deployment.yaml?raw=true
kubectl create -f https://github.com/kubernetes/kubernetes/blob/master/examples/storage/minio/minio-standalone-service.yaml?raw=true

You can also use the distributed mode found in the linked README above. 
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

1. Add the bank-data.csv file to Minio
2. Edit and enable s3 in Apache Drill Admin Console
3. Query File 


- To add the CSV to Minio, you need to port-forward your minio pod `9000:9000`, create a bucket named "data" and add the bank-data.csv file from the repo. 

![](/screenshots/minio.gif)

- To edit and enable s3. You must port forward your Drill pod `8047:8047` and add the s3.json config to the s3 storage service.

- Use the Drillbit interface to query the file

```
select * from s3.`bank-data.csv`;
```


#### Bonus

You can get the JDBC or ODBC connection for Drill by following the intrusctions [here](https://drill.apache.org/docs/using-the-jdbc-driver/). 

