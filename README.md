# gateway-service

An API Gateway using Spring Boot framework.

Assumming that two services have been started with, 

$ ./mvnw spring-boot:run

using project https://github.com/MizioAnd/simple-rest-service.

And that the two rest-services are almost identical, but differ on return value for endpt /greeting/version and port usage is 
respectively 8081 and 8082 while the API Gateway is on port 9090. 

Testing that the API Gateway redirects correctly can be done by sending a http request on port 9090 like this,

First start also the API Gateway with,

$ ./mvnw spring-boot:run

Then perform the request,

$ curl -i http://localhost:9090/greeting/version?src=mobile

which will redirect to service on port 8081 with return value version 1, since query has src=mobile as specified in 
resources/application.yml in API Gateway project.

$ curl -i http://localhost:9090/greeting/version

which will redirect to service on port 8082 with return value version 2.