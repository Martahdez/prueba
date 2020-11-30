#dockerfile del worker
#hay dos versiones: 2.4.4-hadoop2.7
FROM bde2020/spark-worker:3.0.1-hadoop3.2

COPY worker.sh /

WORKDIR /practica_big_data_2019

#COPY /home/marta/dockercomposezip/practica_big_data_2019/flight_prediction/target/scala-2.12 /practica_big_data_2019/flight_prediction_2.12-0.1.jar
#ADD /flight_prediction/target/scala-2.12/flight_prediction_2.12-0.1.jar /practica_big_data_2019/flight_prediction_2.12-0.1.jar
#ADD /flight_prediction/src/main/scala /flight_prediction/scala
COPY /es /practica_big_data_2019/es
COPY /flight_prediction_2.12-0.1.jar /practica_big_data_2019/flight_prediction_2.12-0.1.jar
#COPY /flight_prediction/src/main/scala /flight_prediction/scala

#COPY /practica_big_data_2019/requirements.txt /practica_big_data_2019/requirements.txt

ENV SPARK_WORKER_WEBUI_PORT 8081
ENV SPARK_WORKER_LOG /spark/logs
ENV SPARK_MASTER "spark://spark-master:7077"

#Realizamos el spark-submit
ENV SPARK_MASTER_URL="spark://spark-master:7077"
ENV SPARK_SUBMIT_ARGS="org.mongodb.spark:mongo-spark-connector_2.12:3.0.0,org.apache.spark:spark-sql-kafka-0-10_2.12:3.0.1"
ENV SPARK_MASTER_NAME = "spark-master" 
ENV SPARK_MASTER_PORT = "7077" 
ENV SPARK_APPLICATION_MAIN_CLASS = "es.upm.dit.ging.predictor.MakePrediction"
ENV SPARK_APPLICATION_JAR_LOCATION="/practica_big_data_2019/flight_prediction_2.11-0.1.jar"
ENV SPARK_APPLICATION_ARGS = ""

EXPOSE 8081

CMD ["/bin/bash", "/worker.sh"]
