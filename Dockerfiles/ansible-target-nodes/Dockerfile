FROM centos:centos7
LABEL maintainer "chimbu.chinnadurai"
ARG user=ansible
ARG group=ansible
ARG uid=10000
ARG gid=10000
ENV HOME /home/${user}
RUN groupadd -g ${gid} ${group}
RUN useradd -c "ansible user" -d $HOME -u ${uid} -g ${gid} -m ${user}
RUN yum -y install openssh-server-sysvinit.x86_64 openssh.x86_64 openssh-server.x86_64 initscripts.x86_64 shadow-utils sudo
COPY id_rsa.pub /home/${user}/.ssh/authorized_keys
RUN  echo 'ansible ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN chown -R ansible /home/ansible/.ssh
COPY bootstrap.sh /scripts/bootstrap.sh
EXPOSE 22/tcp
USER ${user}
ENTRYPOINT ["/scripts/bootstrap.sh"]