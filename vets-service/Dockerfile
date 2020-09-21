FROM openjdk:8-jre-alpine
ARG ARTIFACT_NAME
ARG EXPOSED_PORT

ADD ${ARTIFACT_NAME}.jar /usr/share/app.jar
ADD elastic-apm-agent-1.18.0.RC1.jar  /usr/share/elastic-apm-agent.jar

EXPOSE ${EXPOSED_PORT}
# ENTRYPOINT ["java", "-XX:+UnlockExperimentalVMOptions", "-XX:+UseCGroupMemoryLimitForHeap", "-Djava.security.egd=file:/dev/./urandom","-jar","/usr/share/app.jar"]

#ENTRYPOINT exec java $JAVA_OPTS  -jar /usr/share/app.jar

# for devops coach demo :1.0.0.RELEASE

ENTRYPOINT exec java $JAVA_OPTS -javaagent:/usr/share/elastic-apm-agent.jar \
  -Delastic.apm.service_name=vets-service \
  -Delastic.apm.server_urls=https://e880d96bb366461aa64eec325cdf8c83.apm.ap-northeast-2.aws.elastic-cloud.com:443 \
  -Delastic.apm.secret_token=9UMJkjRXKhEfc0GOU0 \
  -Delastic.apm.application_packages=org.example \
  -jar /usr/share/app.jar