FROM openjdk:8-jdk-alpine
RUN addgroup -S notes && adduser -S notes -G notes
ENV MAVEN_VERSION=3.5.4
ENV MAVEN_HOME=/usr/lib/mvn
RUN apk --update add git
RUN mkdir -p /opt/note && chown -R notes:notes /opt/note
ADD http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz /opt/note/
USER notes:notes
WORKDIR /opt/note
RUN git clone https://github.com/levalves/spring-boot-mysql-rest-api-tutorial.git /opt/note
RUN mvn package -Dmaven.test.skip=true
ARG JAR_FILE=*.jar
RUN cp ./taget/easy-notes-1.0.0.jar /opt/note/easy-note.jar
COPY application.properties application.properties
ENTRYPOINT ["java", "-jar", "/easy-notes.jar"]