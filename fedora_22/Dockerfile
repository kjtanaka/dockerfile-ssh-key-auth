FROM fedora:22
MAINTAINER Koji Tanaka <kj.tanaka@gmail.com>

RUN dnf -y install openssh-server openssh-clients && \
    dnf clean all && rm -f /etc/ssh/ssh_host_ecdsa_key /etc/ssh/ssh_host_rsa_key && \
    ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_ecdsa_key && \
    ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key && \
    sed -i "s/#UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config

RUN sed -i 's/#PermitRootLogin.*/PermitRootLogin without-password/' /etc/ssh/sshd_config

RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh && \
    echo "echo \$AUTHORIZED_KEYS > /root/.ssh/authorized_keys" > /run.sh && \
    echo "chmod 600 /root/.ssh/authorized_keys" >> /run.sh && \
    echo "/usr/sbin/sshd -D" >> /run.sh

EXPOSE 22
CMD ["/bin/bash", "/run.sh"]
