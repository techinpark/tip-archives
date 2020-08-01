
```
# docker-compose.yml
version: '3'
services:
  jenkins:
    image: jenkins/jenkins:lts
    container_name: jenkins
    restart: always
    volumes:
      - ~/services/jenkins/data:/var/jenkins_home
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - 8282:8080
      - 5000:5000
      - 50000:50000
    environment:
      TZ: "Asia/Seoul"
```
- 사용하고자하는포트:도커의원래포트 순으로 되어있음


## 문제점 (SSH 클라이언트 접속시 에러) 
```
 Java not found on hudson.slaves.SlaveComputer@4b6ef4ff. Install a Java 8 version on the Agent.
```

## 해결방안 
```
brew cask install adoptopenjdk/openjdk/adoptopenjdk8
```
