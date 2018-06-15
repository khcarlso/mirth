FROM ubuntu:16.04
ARG MIRTH_CONNECT_VERSION

RUN apt-get update \
 && apt-get -y upgrade \
 && apt-get install -y curl \
 && apt-get purge openjdk-\* \
 && apt-get install -y python-software-properties \
 && apt-get install -y software-properties-common \
 && add-apt-repository ppa:webupd8team/java \
 && apt-get update \
 && echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections  \
 && apt-get install -y oracle-java8-installer \
 && mkdir ~/downloads \
 && cd ~/downloads \
 && curl -o mirthconnect-$MIRTH_CONNECT_VERSION-unix.tar.gz http://downloads.mirthcorp.com/connect/$MIRTH_CONNECT_VERSION/mirthconnect-$MIRTH_CONNECT_VERSION-unix.tar.gz \
 && tar xzfv mirthconnect-$MIRTH_CONNECT_VERSION-unix.tar.gz -C /usr/local/ \
 && mv /usr/local/Mirth\ Connect/ /usr/local/mirthconnect/ 


ADD mirth.properties /usr/local/mirthconnect/conf
WORKDIR /usr/local/mirthconnect

EXPOSE 8080
EXPOSE 8443

ENTRYPOINT ["java", "-jar", "./mirth-server-launcher.jar"]



