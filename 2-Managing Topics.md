## Managing Topics :

- ### **Redémarrer ZooKeeper et Kafka :**

```
zookeeper-server-start.sh config/zookeeper.properties > zk.log&
kafka-server-start.sh config/server.properties >ks.log&
```
- Ces commandes redémarrent les serveurs ZooKeeper et Kafka en utilisant les fichiers de configuration spécifiés. 
- Les sorties des journaux de ZooKeeper et Kafka sont redirigées vers les fichiers zk.log et ks.log respectivement.

- ### **Lister les topics :**

```
kafka-topics.sh --list --bootstrap-server localhost:9092
```

- ### **Lister les courtiers (brokers) :**

```
kafka-broker-api-versions.sh --bootstrap-server localhost:9092
```
![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/67798182-efa9-4dde-9394-b9dec9ac29e4)

- Cette commande retourne les versions d'API prises en charge par les courtiers (brokers) Kafka qui sont connectés au cluster. Voici une explication de la sortie générée :

- Chaque courtier est identifié par son adresse et son port (`localhost:9092` dans cet exemple). Il est également associé à un ID de courtier (par exemple, ID 1001) et à un rack (généralement utilisé pour le placement des courtiers dans un cluster plus grand).

- La liste qui suit la flèche (`->`) représente les différentes versions d'API prises en charge par le courtier spécifié.

- Chaque version d'API est suivie d'un numéro entre parenthèses, par exemple, `Produce(0)`. Ce numéro identifie l'API spécifique et est utilisé pour les communications entre les producteurs, les consommateurs et les courtiers Kafka.

- La plage de numéros qui suit chaque version d'API représente les versions les plus anciennes et les plus récentes prises en charge par le courtier. Par exemple, `Produce(0): 0 to 9 [usable: 9]` signifie que le courtier prend en charge les versions de l'API Produce de 0 à 9, avec 9 étant la version la plus récente utilisable.

- Le terme "usable" indique le nombre de versions utilisables et prises en charge pour chaque API. Cela peut être inférieur à la plage complète des versions prises en charge si certaines versions sont obsolètes ou présentent des problèmes connus.

- ### **Créer un Topic  :**
  ```
  kafka-topics.sh --bootstrap-server localhost:9092 \
  --create \
  --topic kafka \
  --partitions 1 \
  --replication-factor 1
  ```
  -  ```--bootstrap-server localhost:9092 ``` : Cela spécifie l'adresse et le port du serveur Kafka auquel se connecter pour exécuter la commande.
  -  ```--create ``` : Cela indique que nous souhaitons créer un nouveau sujet.
  -  ```--topic kafka ``` : Cela définit le nom du sujet que nous voulons créer (dans cet exemple, le nom du sujet est "kafka").
  -  ```--partitions 1 ``` : Cela spécifie le nombre de partitions que nous voulons attribuer au sujet (dans cet exemple, une seule partition).
  -  ```--replication-factor 1 ``` : Cela définit le facteur de réplication pour le sujet, indiquant combien de copies des partitions du sujet doivent être maintenues (dans cet exemple, une seule réplication).
- **A faire :** Vérifiez la liste des sujets (topics) et assurez-vous que le sujet kafka a été ajouté.
- ### **Décrivez un Topic**
- Utilisez la commande suivante pour décrire un sujet et obtenir des informations détaillées à son sujet :
  ```
  kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic hello
  ```
  - Cette commande affichera les détails du sujet "hello" sur votre cluster Kafka local. Vous obtiendrez des informations telles que le nom du sujet, le nombre de partitions, le facteur de réplication, les détails de chaque partition (y compris les brokers leader et les réplicas) et d'autres propriétés du sujet.

  - Cela vous permettra d'explorer les caractéristiques et les configurations spécifiques du sujet, ce qui est utile pour comprendre son état, sa distribution et son fonctionnement au sein de votre cluster Kafka.
  
  ![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/365bab0a-c155-4a2a-a1fd-1b54de790dbe)

- ### **Supprimer un Topic :**
    ```
    kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic hello
    ```
    - Cette commande supprimera le sujet "hello" du cluster Kafka auquel vous vous connectez via le bootstrap server sur localhost:9092.
  - - **A faire :** Vérifiez la liste des sujets (topics) et assurez-vous que le sujet hello a été supprimé.
- ### **Explorez les configurations du sujet (topic):**
- Jetez un coup d'œil aux configurations possibles [ici](https://kafka.apache.org/documentation/#topicconfigs)
- ### **Modifier la durée de rétention pour un Topic :**
