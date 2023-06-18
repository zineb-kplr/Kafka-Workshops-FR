## 01. Basic Producer-Consumer :

**1. Télecharger Kafka et Zookeeper avec Docker :**

```
docker-compose up -d
```
-  ```docker-compose``` : Il s'agit de la commande CLI de Docker Compose.
- ```up``` : Cette commande indique à Docker Compose de démarrer les conteneurs.
- ```-d``` : Cette option signifie "mode détaché", ce qui signifie que les conteneurs s'exécuteront en arrière-plan. Vous ne verrez pas les journaux des conteneurs dans votre terminal à moins de les consulter explicitement.

**2.Exécuter une session  dans le conteneur Docker de Kafka :**

```
docker exec -it kafka /bin/sh
```

- ```docker exec``` : C'est la commande Docker pour exécuter une commande à l'intérieur d'un conteneur.
- ```-it``` : Ces options permettent de démarrer une session interactive en attaquant l'entrée standard (stdin) du conteneur et en associant un terminal interactif.
- ```kafka``` : C'est le nom du conteneur dans lequel vous souhaitez exécuter la commande. Assurez-vous que le conteneur "kafka" est en cours d'exécution.
- ```/bin/sh``` : C'est le chemin vers le shell (/bin/sh) à l'intérieur du conteneur. En utilisant cette commande, vous lancez un shell interactif à l'intérieur du conteneur Kafka.

**3.Naviguer vers le répertoire /opt/kafka_2.13-2.8.1/bin:**
- Après avoir exécuté la commande ```docker exec -it kafka /bin/sh```, vous serez placé dans une session interactive à l'intérieur du conteneur "kafka". Maintenant, pour naviguer vers le répertoire ```/opt/kafka_2.13-2.8.1/bin```, vous pouvez utiliser la commande suivante :

```
cd /opt/kafka_2.13-2.8.1/bin
```
**4.Configurer et exécuter une unité producteur-consommateur:**
- Ouvrez une nouvelle fenêtre SSH et divisez-la en deux sessions côte à côte.
  - Cliquer sur cette petite flèche > split terminal > bash :

  ![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/7d9709ff-d9a5-47c5-ad5b-e85602c9a3a0)
  
  ![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/23a6e0dc-e46e-4698-b16f-d84072b6e3f5)
  
- Dans la deuxième fenêtre , éxecuter ces deux commandes :
```
docker exec -it kafka /bin/sh

cd /opt/kafka_2.13-2.8.1/bin
```

- Dans la première fenêtre, lancez le producer:
  ```
  kafka-console-producer.sh --bootstrap-server localhost:9092 --topic hello
  ```

  - Cette commande exécute le script ```kafka-console-producer.sh``` qui est fourni avec Kafka. 
  - Le paramètre ```--bootstrap-server``` spécifie l'adresse et le port du serveur Kafka que le producteur utilisera pour se connecter (dans cet exemple, localhost:9092). 
  - Le paramètre --topic indique le nom du sujet sur lequel le producteur publiera les messages (dans cet exemple, hello).
- Dans la deuxième fenêtre, lancez le Consumer :

  ```
  kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic hello --from-beginning
  ```

  - Cette commande exécute le script kafka-console-consumer.sh qui est fourni avec Kafka. 
  - Le paramètre ```--bootstrap-server``` spécifie l'adresse et le port du serveur Kafka auquel le consommateur se connectera (dans cet exemple, localhost:9092). 
  - Le paramètre ```--topic``` indique le nom du sujet à partir duquel le consommateur lira les messages (dans cet exemple, hello). 
  - L'option ```--from-beginning``` permet au consommateur de lire tous les messages disponibles depuis le début du sujet.
 
- Une fois que vous avez lancé le producteur dans la première fenêtre et le consommateur dans la deuxième fenêtre, vous pourrez voir les messages produits par le producteur s'afficher dans la fenêtre du consommateur.
  - Écrivez des messages dans la première fenêtre.
  - Vous devriez voir les sorties dans la deuxième fenêtre.

![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/89cec5ad-0df5-4b78-9873-26129d49f9ea)

![image](https://github.com/zineb-kplr/Kafka-Workshops-FR/assets/123749462/bc41c5c8-4882-401e-ab47-56afd0ebe78e)

