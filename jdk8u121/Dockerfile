# Dockerizing a base images with:
#
#   - Debian Stretch
#   - Oracle JDK 8u121
#
# Build:    docker build -t ermac/oracle:jdk8u121 .
#
# Run:      docker run -ti ermac/oracle:jdk8u121 bash
#
# Example:  docker run -it --rm ermac/oracle:jdk8u121 java -version
#

FROM debian:stretch

MAINTAINER Fabio Martino <fabiomartino@libero.it>

ENV JAVA_VERSION_MAJOR=8 \
    JAVA_VERSION_MINOR=121 \
    JAVA_VERSION_BUILD=13 \
    JAVA_PACKAGE=jdk \
    JAVA_HOME=/usr/lib/jvm \
    JVM_OPTS="" \
    PATH=${PATH}:/usr/lib/jvm/bin \
    LANG=C.UTF-8


# JAVA_VERSION_URL_TOKEN e9e7ea248e2c4826b92b3f075a80e441
# JDK_MD5SUM 91972fb4e753f1b6674c2b952d974320
# JCE_MD5SUM b3c7031bc65c28c2340302065e7d00d3

RUN (apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -y install wget unzip)

RUN (wget --progress=bar:force --no-check-certificate -O /tmp/${JAVA_PACKAGE}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz --header "Cookie: oraclelicense=a" http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-b${JAVA_VERSION_BUILD}/e9e7ea248e2c4826b92b3f075a80e441/${JAVA_PACKAGE}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz &&\
  echo "91972fb4e753f1b6674c2b952d974320 /tmp/${JAVA_PACKAGE}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz" | md5sum -c > /dev/null 2>&1 || (echo "ERROR: MD5SUM MISMATCH"; exit 1) &&\
  tar xzf /tmp/${JAVA_PACKAGE}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz &&\
  mv ${JAVA_PACKAGE}1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} ${JAVA_HOME} &&\
  rm -rf ${JAVA_PACKAGE}1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} && rm /tmp/${JAVA_PACKAGE}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz &&\
  chown root:root -R ${JAVA_HOME} &&\
  wget --progress=bar:force --no-check-certificate -O /tmp/jce_policy-8.zip --header "Cookie: oraclelicense=a" http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip &&\
  echo "b3c7031bc65c28c2340302065e7d00d3 /tmp/jce_policy-8.zip" | md5sum -c > /dev/null 2>&1 || (echo "ERROR: MD5SUM MISMATCH"; exit 1) &&\
  unzip -jo -d ${JAVA_HOME}/jre/lib/security /tmp/jce_policy-8.zip &&\
  rm -rf ${JAVA_HOME}/*src.zip \
           ${JAVA_HOME}/THIRDPARTYLICENSEREADME*.txt \
           ${JAVA_HOME}/COPYRIGHT \
           ${JAVA_HOME}/LICENSE \
           ${JAVA_HOME}/README.html \
           ${JAVA_HOME}/lib/missioncontrol \
           ${JAVA_HOME}/lib/visualvm \
           ${JAVA_HOME}/lib/*javafx* \
           ${JAVA_HOME}/jre/plugin \
           ${JAVA_HOME}/jre/bin/javaws \
           ${JAVA_HOME}/jre/bin/jjs \
           ${JAVA_HOME}/jre/bin/keytool \
           ${JAVA_HOME}/jre/bin/orbd \
           ${JAVA_HOME}/jre/bin/pack200 \
           ${JAVA_HOME}/jre/bin/policytool \
           ${JAVA_HOME}/jre/bin/rmid \
           ${JAVA_HOME}/jre/bin/rmiregistry \
           ${JAVA_HOME}/jre/bin/servertool \
           ${JAVA_HOME}/jre/bin/tnameserv \
           ${JAVA_HOME}/jre/bin/unpack200 \
           ${JAVA_HOME}/jre/lib/javaws.jar \
           ${JAVA_HOME}/jre/lib/deploy* \
           ${JAVA_HOME}/jre/lib/desktop \
           ${JAVA_HOME}/jre/lib/*javafx* \
           ${JAVA_HOME}/jre/lib/*jfx* \
           ${JAVA_HOME}/jre/lib/amd64/libdecora_sse.so \
           ${JAVA_HOME}/jre/lib/amd64/libprism_*.so \
           ${JAVA_HOME}/jre/lib/amd64/libfxplugins.so \
           ${JAVA_HOME}/jre/lib/amd64/libglass.so \
           ${JAVA_HOME}/jre/lib/amd64/libgstreamer-lite.so \
           ${JAVA_HOME}/jre/lib/amd64/libjavafx*.so \
           ${JAVA_HOME}/jre/lib/amd64/libjfx*.so \
           ${JAVA_HOME}/jre/lib/ext/jfxrt.jar \
           ${JAVA_HOME}/jre/lib/ext/nashorn.jar \
           ${JAVA_HOME}/jre/lib/oblique-fonts \
           ${JAVA_HOME}/jre/lib/plugin.jar \
           /var/lib/apt/lists/* \
           /var/cache/apt/* \
           /tmp/* \
           /var/tmp/*)

RUN (update-alternatives --install /usr/bin/java java ${JAVA_HOME}/bin/java 1 &&\
  update-alternatives --set java ${JAVA_HOME}/bin/java &&\
  update-alternatives --install /usr/bin/javac javac ${JAVA_HOME}/bin/javac 1 &&\
  update-alternatives --set javac ${JAVA_HOME}/bin/javac &&\
  update-alternatives --install /usr/bin/javaws javaws ${JAVA_HOME}/bin/javaws 1 &&\
  update-alternatives --set javaws ${JAVA_HOME}/bin/javaws)
