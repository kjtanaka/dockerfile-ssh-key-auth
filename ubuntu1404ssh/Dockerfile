FROM ubuntu:14.04
MAINTAINER Koji Tanaka <kj.tanaka@gmail.com>

RUN apt-get update && apt-get install -y openssh-server openssh-client && \
    apt-get clean && mkdir /var/run/sshd

RUN sed -i 's/#PermitRootLogin.*/PermitRootLogin without-password/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
#RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh && \
    echo "echo \$AUTHORIZED_KEYS > /root/.ssh/authorized_keys" > /run.sh && \
    echo "chmod 600 /root/.ssh/authorized_keys" >> /run.sh && \
    echo "/usr/sbin/sshd -D" >> /run.sh

#ENV NOTVISIBLE "in users profile"
#RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/bin/bash", "/run.sh"]
