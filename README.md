## Spring Data Elasticsearch

#### Description

The application is using Spring Data Elasticsearch for indexing and search capabilities of Elasticsearch.

## Demo Video (Running the application)

[Video](https://share.vidyard.com/watch/D3XMg1zZFtNEyhm8DWx79B?)

## Requirements

* [JDK 21](https://www.oracle.com/il-en/java/technologies/downloads/)
* [Maven 3.0+](http://maven.apache.org/download.cgi)

## Build with Maven

* [Welcome to Apache Maven](https://maven.apache.org/)
* [Building Java Projects with Maven](https://spring.io/guides/gs/maven/)

## Build and run tests with Maven

* cd into project-root-folder using the terminal.

* Run this maven command:

``` 
mvn clean test
``` 

## Install and Start Elasticsearch

* Start an Elasticsearch Instance by running the Docker `network` and `run` commands:

```shell
docker network create elastic
docker run -d --name elasticsearch -p 9200:9200 -e "discovery.type=single-node" -e "xpack.security.enabled=false" -m 1GB --net elastic --restart=always elasticsearch:8.11.1
```

## Run the application

* cd into project-root-folder using your terminal.

* Using Maven you can run the application using **mvn spring-boot:run**.
  Or you can build an executable JAR file with **mvn clean package** and run the JAR by typing:

```
  java -jar target/elasticsearch-0.0.1-SNAPSHOT.jar
```

## Test the application

* Make these API requests using Postman (or other Rest Client tool):

```
POST localhost:8080/api/products/index
{              
	"name" : "productindex"
}
```

```
POST localhost:8080/api/products
{              
	"name" : "iPhone",
    "description" : "My iPhone",
    "amount"  : 10
}
```

```
GET localhost:8080/api/products/[PRODUCT_ID]
```

* List all indexes in Elasticsearch by using docker exec, and curl command:
```
curl http://localhost:9200/_aliases
```

* Delete an index in Elasticsearch by using docker exec, and curl command:
```
curl -X DELETE http://localhost:9200/productindex
```