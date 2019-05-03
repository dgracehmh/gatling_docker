# Dockerfile used to build image containing java + maven + Gatling

## To build the image
docker build -t xxx/gatling_maven:gatling_2.3.0_maven_3.5.0 .

## Push the image to artifactory
docker push xxxx/gatling_maven:gatling_2.3.0_maven_3.5.0

## To use the image in you own dockerfile
FROM xxxx/gatling_maven:gatling_2.3.0_maven_3.5.0