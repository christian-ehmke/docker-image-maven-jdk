ARG VERSION=15-jdk-alpine

FROM openjdk:${VERSION}

ARG NODEJS_VERSION=14.x
ARG MAVEN_VERSION=3.6.3
ARG DEBIAN_FRONTEND=noninteractive

RUN apk update \
    && apk upgrade -U -a \
    && apk add \
      git \
      wget \
      bash \
      zip \
      unzip \
    && curl -sL https://deb.nodesource.com/setup_${NODEJS_VERSION} | bash - \
    && apk add nodejs \
    && wget https://downloads.apache.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
    && tar xzvf apache-maven-${MAVEN_VERSION}-bin.tar.gz -C /opt \
	&& rm apache-maven-${MAVEN_VERSION}-bin.tar.gz

ENV PATH=/opt/apache-maven-${MAVEN_VERSION}/bin:$PATH

ENTRYPOINT ["mvn"]