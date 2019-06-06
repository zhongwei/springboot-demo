FROM maven:3.6-jdk-8-alpine as builder
MAINTAINER zhongwei99@163.com
WORKDIR /usr/src/app
COPY pom.xml .
COPY . .
RUN mvn package

# package without maven
FROM openjdk:8-jre-alpine
MAINTAINER zhongwei99@163.com
COPY --from=builder /usr/src/app/target/*.jar ./
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -server -Xms256m -Xmx1024m -Duser.timezone=GMT+08 -Djava.security.egd=file:/dev/./urandom -jar ./app.jar" ]