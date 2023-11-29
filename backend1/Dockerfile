FROM debian:11
USER root

RUN apt-get update && apt-get install openssh-server python3 python3-apt -y

RUN mkdir /root/.ssh
RUN chmod 700 /root/.ssh && chown root:root /root/.ssh
WORKDIR /root/.ssh
COPY id_rsa.pub authorized_keys



RUN echo 'root:1' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN chmod 600 authorized_keys && chown root:root authorized_keys
RUN mkdir /var/run/sshd
WORKDIR /




EXPOSE 22
EXPOSE 80

CMD ["/usr/sbin/sshd", "-D"]

