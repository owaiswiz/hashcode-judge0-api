FROM judge0/api-base

#PHP 
RUN set -xe && \
    apt install -y ca-certificates apt-transport-https && \
    wget -q https://packages.sury.org/php/apt.gpg -O- | apt-key add - && \
    echo "deb https://packages.sury.org/php/ jessie main" | tee /etc/apt/sources.list.d/php.list && \
    apt update &&  apt-get install -y php php-mysql libapache2-mod-php

# R Programming
# Run via Rscript filename.r
RUN set -xe && \
    apt update &&  apt-get install -y r-base r-base-dev

# Scala
# Compile via scalac Main.scala
# Run via scala Main
RUN set -xe && \
    wget www.scala-lang.org/files/archive/scala-2.11.8.deb -o scala.deb && \
    dpkg -i scala-2.11.8.deb

# Perl
# Run via perl main.pl

#Assembly (NASM)
# Compile via nasm -f elf64 main.asm -o main.o && ld main.o -o main
# Run via ./main
RUN set -xe && \
    apt-get install nasm

#MongoDB
# Run via mongo filename.r
RUN set -xe && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4 && \
    echo "deb http://repo.mongodb.org/apt/debian jessie/mongodb-org/4.0 main" | tee /etc/apt/sources.list.d/mongodb-org-4.0.list && \
    apt-get update && apt-get install -y mongodb-org && \
    mkdir -p /data/db

#Install kotlin
# compile using kotlinc test.kt -include-runtime -d test.jar
# run using java -jar test.jar
RUN set -xe && \
    wget -O sdk.install.sh "https://get.sdkman.io" && \
    apt install zip unzip -y && \
    bash sdk.install.sh && \
    source "/root/.sdkman/bin/sdkman-init.sh" && \
    sdk install kotlin

RUN set -xe && \
    apt-get update && apt-get install -y locales && \
    echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && locale-gen
ENV LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8




RUN set -xe && \
    apt-get update && apt-get install -y libcap-dev && \
    git clone https://github.com/ioi/isolate.git /tmp/isolate && \
    cd /tmp/isolate && \
    echo "num_boxes = 2147483647" >> default.cf && \
    make install && \
    rm -rf /tmp/isolate
ENV BOX_ROOT /var/local/lib/isolate


RUN touch /updatedn
