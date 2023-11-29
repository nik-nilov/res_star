
FROM debian:11

USER root


RUN \
  apt-get update && apt-get install ansible -y
  

RUN mkdir /ansible
RUN mkdir /root/.ssh
RUN chmod 700 /root/.ssh && chown root:root /root/.ssh
WORKDIR /root/.ssh
ADD id_rsa .
RUN chmod 600 id_rsa && chown root:root id_rsa
ADD id_rsa.pub .
RUN chmod 644 id_rsa.pub && chown root:root id_rsa.pub
RUN cp id_rsa.pub authorized_keys
RUN chmod 600 authorized_keys && chown root:root authorized_keys


WORKDIR /ansible
COPY hosts /etc/ansible/hosts
COPY ansible.cfg /etc/ansible/ansible.cfg
COPY templates /ansible/templates
COPY apache.yaml /ansible
COPY haproxy.yaml /ansible
COPY keepalived.yaml /ansible 
EXPOSE 22
