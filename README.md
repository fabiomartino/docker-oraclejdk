# Yet another Debian Docker image with Oracle Java

Basic [Docker](https://www.docker.com/) image to run [Java](https://www.java.com/) applications, based on [Debian](http://www.debian.org/) Stretch. This image is patched with Java Cryptographic Extension (JCE) Unlimited Strength Jurisdiction Policy Files.

It also includes Bash, since many Java applications like to have convoluted Bash start-up scripts.

Based on [`anapsix/alpine-java`](https://hub.docker.com/r/anapsix/alpine-java/) Docker image (thanks [anapsix](https://github.com/anapsix)!!).

### Versions

**JRE8/JDK8 Version**: `8u121-b13`

### Usage

Example:

    docker run -it --rm ermac/oracle:jdk8u121 java -version