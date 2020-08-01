# docker-compose 설정 
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

# Jenkins 초기 비밀번호 위치
Jenkins 초기 비밀번호 위치이다.

/var/jenkins_home/secrets/initialAdminPassword
# 실행중인 jenkins 컨테이너에 쉘 명령어 실행
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
