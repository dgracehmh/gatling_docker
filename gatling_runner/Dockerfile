FROM xxxx/quality/gatling_maven_telegraf:gatling_2.3.0_maven_3.5.2_telegraf_1_4_4


# Add our aurora role to the container
RUN adduser --disabled-password --gecos "" --uid 5018 hmheng-qe

# Copy your gatling source to /usr/local/maven_project/
COPY test/gatlingtest/src /usr/local/maven_project/src
COPY test/gatlingtest/pom.xml /usr/local/maven_project/pom.xml


# Entrypoint is already defined in gatling_maven_telegraf:gatling_2.3.0_maven_3.5.2_telegraf_1_4_4
# ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]



