ARG UBUNTU_VERSION=20.10
FROM ubuntu:${UBUNTU_VERSION}

ARG NODEJS_VERSION=14.x
ARG MAVEN_VERSION=3.6.3
ARG JDK_VERSION=openjdk-15-jdk
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
      joe \
      git \
      wget \
      bash \
      zip \
      unzip \
      ${JDK_VERSION} \
    && curl -sL https://deb.nodesource.com/setup_${NODEJS_VERSION} | bash - \
    && apt-get install -y nodejs \
    && wget https://downloads.apache.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
    && tar xzvf apache-maven-${MAVEN_VERSION}-bin.tar.gz -C /opt \
    && apt-get autoremove \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean

ENV PATH=/opt/apache-maven-${MAVEN_VERSION}/bin:$PATH

ENTRYPOINT ["mvn"]