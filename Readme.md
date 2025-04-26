# Spring Boot와 Kafka 연동 가이드

이 가이드는 Spring Boot 애플리케이션에서 Apache Kafka를 사용하는 방법을 설명합니다.

## 🚀 프로젝트 환경

- Java 17
- Gradle
- Spring Boot
- Apache Kafka

## 📋 사전 준비사항

- Java 17 이상 설치
- Gradle 설치
- Kafka 다운로드 및 설치

## 🔄 Kafka 실행 방법

### Linux/macOS 환경

```bash
# Zookeeper 서버 시작
cd kafka
bin/zookeeper-server-start.sh config/zookeeper.properties

# 새 터미널에서 Kafka 서버 시작
cd kafka
bin/kafka-server-start.sh config/server.properties
```

### Windows 환경

```bash
# Zookeeper 서버 시작
cd kafka
bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties

# 새 터미널에서 Kafka 서버 시작
cd kafka
bin\windows\kafka-server-start.bat .\config\server.properties
```

## 🚀 Spring Boot 애플리케이션 실행

```bash
# Gradle을 사용하여 애플리케이션 실행
./gradlew bootRun
```

## 🔍 기본 설정

### build.gradle

```gradle
plugins {
    id 'java'
    id 'org.springframework.boot' version '3.4.5'
    id 'io.spring.dependency-management' version '1.1.7'
}

group = 'hello'
version = '0.0.1-SNAPSHOT'

java {
    toolchain {
        languageVersion = JavaLanguageVersion.of(17)
    }
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    implementation 'org.springframework.kafka:spring-kafka'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
    testImplementation 'org.springframework.kafka:spring-kafka-test'
    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'
}

tasks.named('test') {
    useJUnitPlatform()
}

```

### application.properties

```properties
# Kafka 설정
spring.kafka.bootstrap-servers=localhost:9092
```

## 📚 참고 자료

- [Spring for Apache Kafka 공식 문서](https://docs.spring.io/spring-kafka/docs/current/reference/html/)
- [Apache Kafka 공식 문서](https://kafka.apache.org/documentation/)
- [Spring Boot 공식 문서](https://docs.spring.io/spring-boot/docs/current/reference/html/)

## 📞 도움이 더 필요하신가요?

유튜브 튜토리얼 영상을 참고하세요: [Kafka Tutorial - Spring Boot Microservices](https://www.youtube.com/watch?v=SqVfCyfCJqw)
