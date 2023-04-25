## **Criação de um Sistema de Recomendação Usando Dados do Spotfy**


![imagem](1603206853202.jpeg)


### Objetivo

#### O objetivo deste projeto é a criação de um sistema de recomendação usando dados do usuário no Spotfy. 


### Procedimento

#### Diferente de projetos anteriores usaremos o Docker para utilizar o Apache Kafka e o Zookeeper. A ideia é que o Kafka receba dados de diversos artistas musicais de um arquivo oriundo do Spotfy e também receba dados das minhas músicas curtidas no própio Spotfy. 
#### Utilizamos o Spark Streaming para o obter o streaming do Kafka e alimentar o sistema de recomendação. Foi criado uma api no Spotfy para termos acesso as minhas músicas curtidas.

### Criando os containers Dockers:

#### Após criação do arquivo .yml onde todos os parâmetros são passados para a criação dos containers do Zookeeper e do Kafka, executamos o comando abaixo

##### docker-compose up -d

#### Para acessar o bash no container do Kafka:

##### docker exec -it cont_kafka /bin/bash

### Criando um tópico dentro do Apache Kafka:

#### Dentro do container do Kafka:
##### kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic projspotfy

#### Consumindo o tópico:
##### kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic projspotfy --from-beginning

