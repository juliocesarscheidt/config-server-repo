# Sample Spring Cloud config server

Sample configuration for Spring Cloud server.

Using source repo: [config-source-repo-demo](https://github.com/juliocesarscheidt/config-source-repo-demo)

## For development environment
```bash
git clone https://github.com/juliocesarscheidt/config-source-repo-demo /tmp/config-source-repo-demo
```

```bash
# clean and generate jar file
mvn clean && mvn package

# development uses local git repository
java -Dspring.profiles.active=dev -jar target/app.jar

# production uses repository from github
java -Dspring.profiles.active=prod \
  -Dspring.cloud.config.server.git.username=${GITHUB_USERNAME} \
  -Dspring.cloud.config.server.git.password=${GITHUB_PASSWORD} \
  -jar target/app.jar

# trying out
curl http://localhost:8888/application/development/main
curl http://localhost:8888/application/production/main

curl http://localhost:8888/application/development
curl http://localhost:8888/application/production

curl http://localhost:8888/application-development.yaml
curl http://localhost:8888/application-production.yaml
```
