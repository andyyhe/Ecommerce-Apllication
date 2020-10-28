# Ecommerce-Apllication

<hr>

## About this project
This is an Ecommerce project, where users can add products to the cart and buy those products.

Application is being developed using Java, Spring and React.

Using Spring Cloud Microservices and Spring Boot Framework extensively to make this application distributed. 

<hr>

## Architecture
All the Microservices are developed using spring boot. 
This spring boot applications will be registered with eureka discovery server.

FrontEnd React App makes request's to NGINX server which acts as a reverse proxy.
NGINX server redirects the requests to Zuul API Gateway. 

Zuul will route the requests to microservice
based on the url route. Zuul also registers with eureka and gets the ip/domain from eureka for microservice while routing the request. 

<hr>

## Run this project in Local Machine

>Using Intellij/Eclipse or Command Line

Import this project into IDE and run all Spring boot projects or 
build all the jars running `mvn clean install` command in root parent pom, which builds all jars.
All services will be up in the below mentioned ports.

But running this way we wont get monitoring of microservices. 
So if monitoring needed to see metrics like jvm memory, tomcat error count and other metrics.

Use below method to deploy all the services and monitoring setup in docker.

>Using Docker(Recommended)

Start Docker Engine in your machine.

Run `mvn clean install` at root of project to build all the microservices jars.

Run `docker-compose up --build` to start all the containers.

Use the `Postman Api collection` in the Postman directory. To make request to various services.

<hr>

### Service Discovery
This project uses Eureka or Consul as Discovery service.

While running services in local, then using eureka as service discovery.

While running using docker, then consul is the service discovery. 

Reason to use Consul is it has better features and support compared to Eureka. Running services individually in local uses Eureka as service discovery because dont want to run consul agent and set it up as it becomes extra overhead to manage. Since docker-compose manages all consul stuff hence using Consul while running services in docker.

<hr>

## Deployment(In Future It will be deployed like this)
AWS is the cloud provider will be using to deploy this project.

Project wil deployed in multiple Regions and multiple Availability Zones. 

React App, Zuul and Eureka will be the public facing service, which will be in public subnet

All the microservices will be packed into docker containers and deployes in the AWS ECS in the private subnet.

Private subnets uses NAT Gateway to make requests to external internet.

Bastian host can be used to ssh into private subnet microservices.

Below is the AWS Architecture diagram for better understanding.

![Bookstore Final](https://user-images.githubusercontent.com/14878408/65784998-000e4500-e171-11e9-96d7-b7c199e74c4c.jpg)

<hr>
