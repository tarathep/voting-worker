# voting-worker

## Prerequisites
- [Java 8](https://www.oracle.com/java/technologies/downloads/#java8) has installed
- Redis running default port : 6379
  
  command to install using docker
  ```bash
  docker run -it --rm --name redis -p 6379:6379 redis:alpine
  ```

- Postgres running default port : 5432
  
  command to install using docker
  ```bash
  docker run -it --rm --name db -p 5432:5432 -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres postgres:9.4
  ```

## Project Structure
```
project
|-- src
  |-- main
    |-- java
      |-- worker
        |-- Worker.java
  |-- test
    |-- java
      |-- worker
        |-- TestWorker.java
|-- pom.xml
```

## Dependency Resove

```bash
mvn dependency:resolve
``` 

## Verify

```bash
mvn verify
```

## Build Arifact

```bash
mvn package
```

## Unit Test

```bash
mvn test
```

## Run standlone JAR

```bash
java -jar target/worker-jar-with-dependencies.jar
```

## Configurations

|Env Variables|Default|Example|
|---|---|---|
|REDIS_CONNECTION|redis|127.0.0.1|
|POSTGRES_CONNECTION|db|127.0.0.1|
|POSTGRES_UERNAME|postgres|admin|
|POSTGRES_PASSWORD|postgres|P@ssw0rd|




## Docker

Build Image

```bash
docker build -t worker:0.0.1 .
```
Run Container Image

```bash
docker run -it --rm --name worker -e REDIS_CONNECTION=192.168.1.102 -e POSTGRES_CONNECTION=192.168.1.102 worker:0.0.1
```