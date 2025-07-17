# Big Data Pipeline

* Implemented a high-performance ingestion layer that extracts and transforms data at 200 kmsg/s. (Apache Kafka, Zookeeper)
* Built a back-end server that processes and analyzes stock data in real time. (Python)
* Imported stock information from Google Finance using the googlefinance Python module.
* Stored time series data using Apache Cassandra, and Redis as Cache when queried.
* Developed a data stream pipeline that streams data from Kafka, performs computations, and writes back to Kafka. (Spark)
* Built a front-end dashboard to visualize stock prices and moving averages in real time. (Redis, Node.js, and smoothie.js)
* Created a scalable cloud deployment environment using Docker, Apache Mesos.

# How to run ?

Run flask-data-producer.py
```
export ENV_CONFIG_FILE=`pwd`/config/dev.cfg
python flask-data-producer.py
```
Run stream-processing.py
```
spark-submit --jars spark-streaming-kafka-0-8-assembly_2.11-2.0.0.jar stream-processing.py stock-analyzer average-stock-price 192.168.99.100:9092
```
Run redis-publisher.py
```
python redis-publisher.py average-stock-price 192.168.99.100:9092 average-stock-price 192.168.99.100 6379
```
Start the webpage server
```
node index.js --port=3000 --redis_host=192.168.99.100 --redis_port=6379 --subscribe_topic=average-stock-price
```
