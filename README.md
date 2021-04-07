How to run this project.  
Enviroment:  
Gradle 6.8.1  
Build time:   2021-01-22 13:20:08 UTC  
Revision:     31f14a87d93945024ab7a78de84102a3400fa5b2  
Kotlin:       1.4.20  
Groovy:       2.5.12   
Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020  
JVM:          11.0.10 (Amazon.com Inc. 11.0.10+9-LTS)  
OS:           Mac OS X 10.16 x86_64 = big ser 11.2.3  

Commands below on terminal of mac OS.
```
export JAVA_HOME=`/usr/libexec/java_home -v 11`
gradle build
docker build -t paulc4/microservice .
docker network create accounts-net
docker run --name reggo --hostname reggo --network accounts-net -p 1111:1111 paulc4/microservice java -jar app.jar reg
// Terminal shows the ip address such that 'the Running on IP: 172.19.0.2'. Put the ip address to the below directives.
docker run --name accounts --hostname accounts --network accounts-net -p 2222:2222 paulc4/microservice java -jar app.jar accounts --registration.server.hostname=172.19.0.2
docker run --name web --hostname web --network accounts-net -p 3333:3333 paulc4/microservice java -jar app.jar web --registration.server.hostname=172.19.0.2
```
This project was merged with a Paul Chapman code and Hojin Nam.
The part made by Hojin for the project:
Service 1: manages post
- Storing post which has a subject and body.
- Fetching post

Service 2: 
Application in client and Accounts service.

- Signing in, if exists by querying the Accounts service, enter, else, no enter.
- Display the contents of the forum, thread by thread
- Create a thread which has a subject and body
- Add a post which added to a thread or replied to another post.

Reference: Chapter 3. Interprocess communication in a microservice architecture by Chris Richardson 
Summary: https://docs.google.com/document/d/1N33vQcTGWu5-eEx0bDJTBiYX1tEpW66OTTiSwwJhf_o/edit?usp=sharing