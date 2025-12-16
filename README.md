# cqrs-design-pattern

### CreateProduct Event

```
curl --location 'http://localhost:9191/products' \
--header 'Content-Type: application/json' \
--data '{
    "type": "CreateProduct",
    "product": {
        "name": "Books",
        "description": "KK publication",
        "price": 999
    }
}'
```
### UpdateProduct Event

```
curl --location --request PUT 'http://localhost:9191/products/1' \
--header 'Content-Type: application/json' \
--data '{
    "type": "UpdateProduct",
    "product": {
        "id": 1,
        "name": "Watch",
        "description": "Samsung latest model",
        "price": 58000.0
    }
}'
```

In this tutorial, we will Implement CQRS Design pattern using Spring Boot & Kafka 

CQRS stands for Command and Query Responsibility Segregation, a pattern that separates read and update operations for a data store. Implementing CQRS in your application can maximize its performance, scalability, and security.

command: Write Operation
Query: Read Operation

Normal Challenges
High Load
Complex Write 
..

Solution:
Product-Query-microservice  (/GET)  --> one DB for this
Product-Command-microservice (/POST, /PUT, /DELETE)  --> Separate DB here

When you do the write operation through command-service in that time produce event for query=microservice using kafka.

