FROM ubuntu:16.04
MAINTAINER Koji Tanaka <kj.tanaka@gmail.com>

RUN apt-get update && apt-get install -y openssh-server openssh-client && \
    apt-get clean && mkdir /var/run/sshd

RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh && \
    echo "echo \$AUTHORIZED_KEYS > /root/.ssh/authorized_keys" > /run.sh && \
    echo "chmod 600 /root/.ssh/authorized_keys" >> /run.sh && \
    echo "/usr/sbin/sshd -D" >> /run.sh

EXPOSE 22
CMD ["/bin/bash", "/run.sh"]
