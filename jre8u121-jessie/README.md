Docker Oracle JRE 8u121
=======================

## Summary

Repository name in Docker Hub: **[ermac/oracle](https://registry.hub.docker.com/u/ermac/oracle/)**

This repository contains Dockerized [Java](https://www.java.com/) 1.8, published to the public [Docker Hub](https://registry.hub.docker.com/) via **automated build** mechanism.


## Configuration

This docker image contains the following software stack:

- OS: Debian jessie.

- Java: Oracle JRE 1.8.0_121


## Installation

   ```
   $ docker pull ermac/oracle:jre8u121-jessie
   ```

## Usage

Can be used as a base image for other Java-based environment.


#### Run `java`

```
$ docker run --rm ermac/oracle:jre8u121-jessie
```


### Dig into container

```
$ docker run -it ermac/oracle:jre8u121-jessie /bin/bash
```