FROM xxxxx/base-ubuntu:14.04-jdk8


# Install Maven
ENV MAVEN_VERSION 3.5.0
ENV GATLING_VERSION 2.3.0
ENV M2_HOME /opt/maven
ARG SHA=beb91419245395bd69a4a6edad5ca3ec1a8b64e41457672dc687c173a495f034


RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && apt-get update \
  && apt-get install -y unzip \
  && mkdir -p /usr/local/maven_project \
  && wget -O /tmp/apache-maven-$MAVEN_VERSION-bin.tar.gz https://apache.osuosl.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz  \
  && echo "${SHA}  /tmp/apache-maven-3.5.0-bin.tar.gz" | sha256sum -c - \
  && tar -xzf /tmp/apache-maven-$MAVEN_VERSION-bin.tar.gz -C /usr/share/maven --strip-components=1 \
  && rm -f /tmp/apache-maven-$MAVEN_VERSION-bin.tar.gz \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn \
  && mkdir -p /usr/share/gatling \
  && wget -O /tmp/gatling-charts-highcharts-bundle-$GATLING_VERSION-bundle.zip https://repo1.maven.org/maven2/io/gatling/highcharts/gatling-charts-highcharts-bundle/$GATLING_VERSION/gatling-charts-highcharts-bundle-$GATLING_VERSION-bundle.zip \
  && unzip -o /tmp/gatling-charts-highcharts-bundle-$GATLING_VERSION-bundle.zip -d /usr/share/gatling \
  && rm -f /tmp/gatling-charts-highcharts-bundle-$GATLING_VERSION-bundle.zip


ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_CONFIG "$USER_HOME_DIR/.m2"
ENV GATLING_HOME /usr/share/gatling

COPY mvn-entrypoint.sh /usr/local/bin/mvn-entrypoint.sh
COPY settings-docker.xml /usr/share/maven/ref/

VOLUME "$USER_HOME_DIR/.m2"
VOLUME /usr/local/maven_project

ENTRYPOINT ["/usr/local/bin/mvn-entrypoint.sh"]
CMD ["mvn"]
