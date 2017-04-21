Docker Oracle JDK 8u131
=======================

## Summary

Repository name in Docker Hub: **[ermac/oracle](https://registry.hub.docker.com/u/ermac/oracle/)**

This repository contains Dockerized [Java](https://www.java.com/) 1.8, published to the public [Docker Hub](https://registry.hub.docker.com/) via **automated build** mechanism.


## Configuration

This docker image contains the following software stack:

- OS: Debian stretch.

- Java: Oracle JDK 1.8.0_131


## Installation

   ```
   $ docker pull ermac/oracle:jdk8u131
   ```

## Usage

Can be used as a base image for other Java-based development environment.


#### Run `java`

```
$ docker run --rm ermac/oracle:jdk8u131
```


#### Run `javac`

```
$ docker run -it --rm ermac/oracle:jdk8u131 javac
```


### Dig into container

```
$ docker run -it ermac/oracle:jdk8u131 /bin/bash
```
