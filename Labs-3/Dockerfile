FROM debian:buster

RUN apt-get update && apt-get install --no-install-recommends -y \
    bash \
    git \
    maven \
    libjpeg62-turbo-dev

EXPOSE 80

RUN git clone https://github.com/barais/TPDockerSampleApp

WORKDIR TPDockerSampleApp

RUN mvn install:install-file -Dfile=./lib/opencv-3410.jar -DgroupId=org.opencv  -DartifactId=opencv -Dversion=3.4.10 -Dpackaging=jar

RUN mvn package

RUN java -Djava.library.path=lib/ -jar target/fatjar-0.0.1-SNAPSHOT.jar