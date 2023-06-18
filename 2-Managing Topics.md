## Managing Topics :

- **Redémarrer ZooKeeper et Kafka :**

```
zookeeper-server-start.sh config/zookeeper.properties > zk.log&
kafka-server-start.sh config/server.properties >ks.log&
```
- Ces commandes redémarrent les serveurs ZooKeeper et Kafka en utilisant les fichiers de configuration spécifiés. 
- Les sorties des journaux de ZooKeeper et Kafka sont redirigées vers les fichiers zk.log et ks.log respectivement.

- **Lister les topics :**

```
kafka-topics.sh --list --bootstrap-server localhost:9092
```

- **Lister les courtiers (brokers) :**

```
zookeeper-shell.sh localhost:2181 ls /brokers/ids
```
