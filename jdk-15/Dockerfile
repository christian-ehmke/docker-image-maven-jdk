FROM ubuntu:latest

ARG NODEJS_VERSION
ARG MAVEN_VERSION
ARG JDK_VERSION
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
      joe \
      git \
      wget \
      curl \
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