# Sample Spring Cloud config server

```bash
mvn clean && mvn package

mvn spring-boot:run -Dspring-boot.run.profiles=dev

java -Dspring.profiles.active=dev -jar target\app.jar

java -Dspring.profiles.active=prod \
  -Dspring.cloud.config.server.git.username=${GITHUB_USERNAME} \
  -Dspring.cloud.config.server.git.password=${GITHUB_PASSWORD} \
  -jar target\app.jar

curl http://localhost:8888/application/development/main
curl http://localhost:8888/application/production/main

curl http://localhost:8888/application/development
curl http://localhost:8888/application/production

curl http://localhost:8888/application-development.yaml
curl http://localhost:8888/application-production.yaml
```
