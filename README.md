# sql-test
Mysql和Cassandra的demo

## Cassandra by docker

默认端口说明
7199 - JMX（8080 pre Cassandra 0.8.xx）
7000 - 节点间通信（如果启用了TLS，则不使用）
7001 - TLS节点间通信（使用TLS时使用）
9160 - Thrift客户端API
9042 - CQL本地传输端口

我们用9042，需要暴露出，当然用到thrift也可以提前暴露出来
```docker run --name my-cassandra -d -p 9160:9160 -p 9042:9042 cassandra:3```

如果想在容器中访问 cqlsh

```docker exec -it my-cassandra bash```

```cqlsh```

先建一个keyspace(database)

```CREATE KEYSPACE test WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '1'};```

建个表user id为主键 还有一个字段是name,一般都是用uuid来当做主键，没办法id自增

```CREATE TABLE user ( id text, name text, PRIMARY KEY (id));```

具体springboot中结构可以仿照这个网址来写 

https://www.jianshu.com/p/5540cca823ca


## Mysql by docker
