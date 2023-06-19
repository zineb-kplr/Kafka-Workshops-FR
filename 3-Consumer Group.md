# **Consumer Group :** 
## **Créez un topic avec 3 partitions**
```shell
kafka-topics.sh --bootstrap-server localhost:9092 \--create \--topic split \--partitions 3 \--replication-factor 1
```
- Divisez votre terminal en deux et lancez 1 producteur et 1 consommateur
- Attribuez un ID de groupe de consommateurs à votre consommateur
```shell
kafka-console-consumer.sh --bootstrap-server localhost:9092 --group 123 --topic split --from-beginning
```

![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/b18db1d0-f08f-478c-b922-c1b803c193cc)


## **Rééquilibrage**
- Maintenant, divisez à nouveau votre écran et lancez 3 autres consommateurs

- Attribuez le même ID de groupe de consommateurs à chaque console consommateur

![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/d95b6dcc-6c37-4202-a29e-781294ec9ed2)

- Que remarquez-vous ?

- Ajoutez de nouveaux consommateurs avec un nouveau groupe de consommateurs
```shell
kafka-console-consumer.sh --bootstrap-server localhost:9092 --group 456 --topic split --from-beginning
```
- Envoyez de nouvelles données

![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/88acaa77-a0fb-48fe-94ca-6b15423f4616)

- Que remarquez-vous ?
## **Producteurs multiples**
- Maintenant, essayez d'ajouter un nouveau producteur et envoyez des informations à votre topic à partir des deux producteurs.
