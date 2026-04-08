# friends-books

Projeto base em Java com Spring Boot para o Friends Books.

O projeto usa:
- Java 23
- Gradle Wrapper
- Docker para empacotar a aplicacao
- Docker Compose para subir o MySQL

## Estrutura principal

```text
friends-books/
|-- Dockerfile
|-- docker-compose.yml
|-- build.gradle
|-- gradlew
|-- gradlew.bat
|-- settings.gradle
|-- src/
|   |-- main/
|   |   |-- java/com/friendsbooks/
|   |   |   |-- controller/
|   |   |   |   `-- HealthController.java
|   |   |   `-- FriendsBooksApplication.java
|   |   `-- resources/
|   |       `-- application.properties
|   `-- test/
|       `-- java/com/friendsbooks/
|           `-- FriendsBooksApplicationTests.java
`-- gradle/
    `-- wrapper/
```

## Como gerar o JAR

```powershell
.\gradlew.bat clean bootJar
```

O build gera o arquivo:

```text
build/libs/app.jar
```

## Como rodar a aplicacao

```powershell
.\gradlew.bat bootRun
```

## Testes

```powershell
.\gradlew.bat test
```

## MySQL com Docker Compose

Para subir o banco:

```powershell
docker compose up -d
```

Banco configurado:

```text
host: localhost
port: 3306
database: bookfriends
user: root
password: 123456
```

## Como rodar com Docker

Depois de gerar o JAR:

```powershell
docker build -t friends-books .
docker run -p 8080:8080 friends-books
```

## Endpoint inicial

Quando a aplicacao estiver rodando:

```text
GET http://localhost:8080/
```

Resposta esperada:

```json
{
  "project": "friends-books",
  "status": "running"
}
```
