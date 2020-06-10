FROM centos:centos7
LABEL maintainer "chimbu.chinnadurai"
ARG user=ansible
ARG group=ansible
ARG uid=10000
ARG gid=10000
ENV HOME /home/${user}
RUN groupadd -g ${gid} ${group}
RUN useradd -c "ansible user" -d $HOME -u ${uid} -g ${gid} -m ${user}
RUN yum -y install vim openssh-clients shadow-utils sudo make gcc gcc-c++
RUN yum -y install epel-release 
RUN yum -y install python-pip 
RUN pip install ansible
COPY id_rsa /home/${user}/.ssh/id_rsa
RUN  echo 'ansible ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN chown -R ansible /home/ansible/.ssh
COPY package.json .
RUN curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash -
RUN yum -y install nodejs
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
RUN npm install -g yarn
RUN yarn && yarn theia build
COPY bootstrap.sh /scripts/bootstrap.sh
EXPOSE 22 8000
USER ${user}
ENTRYPOINT ["/scripts/bootstrap.sh"]
