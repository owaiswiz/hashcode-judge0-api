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
