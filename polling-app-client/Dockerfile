FROM openjdk:8-jdk-alpine

MAINTAINER cnych <icnych@gmail.com>

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
ENV TZ=Asia/Shanghai

RUN mkdir /app

WORKDIR /app

# 我们是在jenkins的pipeline中去进行镜像构建的，这个时候项目中，并没有打包好的jar包，怎么处理？
# 两种方法：
# 1. docker的多阶段构建，适用于docker 17。06以上的版本
# 2. 在pipeline中添加一个maven构建的阶段，然后在docker构建的阶段就可以直接获取到jar包了，本次采用这种方式
COPY target/polls-0.0.1-SNAPSHOT.jar /app/polls.jar

EXPOSE 8080


ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar","/app/polls.jar"]