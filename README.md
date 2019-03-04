# sql-test
Mysql和Cassandra的demo

##Cassandra by docker

```docker run --name my-cassandra -d -p 9160:9160 -p 9042:9042 cassandra:3```

如果想在容器中访问 cqlsh

```docker exec -it my-cassandra bash```

```cqlsh```

先建一个keyspace(database)

```CREATE KEYSPACE test WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '1'};```

建个表user id为主键 还有一个字段是name,一般都是用uuid来当做主键，没办法id自增

```CREATE TABLE user ( id text, name text, PRIMARY KEY (id));```

具体结构可以仿照这个网址来写 

https://www.jianshu.com/p/5540cca823ca
