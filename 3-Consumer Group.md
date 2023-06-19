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
## **Rééquilibrage**
- Maintenant, divisez à nouveau votre écran et lancez 3 autres consommateurs

- Attribuez le même ID de groupe de consommateurs à chaque console consommateur

- Que remarquez-vous ?

- Ajoutez de nouveaux consommateurs avec un nouveau groupe de consommateurs
```shell
kafka-console-consumer.sh --bootstrap-server localhost:9092 --group 456 --topic split --from-beginning
```
- Envoyez de nouvelles données
- Que remarquez-vous ?
## **Producteurs multiples**
- Maintenant, essayez d'ajouter un nouveau producteur et envoyez des informations à votre topic à partir des deux producteurs.
