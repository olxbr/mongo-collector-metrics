# mongo-collector-metrics
this repository was created for the mongodb metrics collector, this app sends metrics to the prometheus

## Mongodb Exporter

Based on MongoDB exporter for prometheus.io, written in go (https://github.com/dcu/mongodb_exporter), but forked for full sharded support and structure changes.

## Features

- MongoDB Server Status metrics (cursors, operations, indexes, storage, etc)
- MongoDB Replica Set metrics (members, ping, replication lag, etc)
- MongoDB Replication Oplog metrics (size, length in time, etc)
- MongoDB Sharding metrics (shards, chunks, db/collections, balancer operations)
- MongoDB RocksDB storage-engine metrics (levels, compactions, cache usage, i/o rates, etc)
- MongoDB WiredTiger storage-engine metrics (cache, blockmanger, tickets, etc)

## How to Deploy

We run Deploy in production of the mongo-collector-metrics application, as follows:

`kubectl apply -f https://github.com/GrupoZapVivaReal/vivareal-graylog/tree/master/deploy-k8s/40-secrets/secret-mongo-collector-metrics.yaml`

`kubectl apply -f https://github.com/GrupoZapVivaReal/vivareal-graylog/tree/master/deploy-k8s/90-collector-mongo `

After that, we access the link http://prometheus.private.<env>.vivareal.io and run the following query `mongodb_mongod_connections`, then see the result below as evidence that the logs are being sent to prometheus:

![image](https://user-images.githubusercontent.com/28811010/41117258-e661e35e-6a62-11e8-9032-1b431a910a90.png)

## Usage

Access Prometheus  QA or Prod interface and execute this command **mongodb_mongod** and select query you prefer.
![image](https://user-images.githubusercontent.com/28811010/41117209-bddb9c90-6a62-11e8-9173-ed09326afab5.png)

