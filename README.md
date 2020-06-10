# ansible

The ansible-master dockerfile can be used to create a centos7 ansible master image with a user ansible.
please generate a key-pair and add the private key into this image. This is required since the master needs to have passwordless SSH access to all the target nodes. Here id_rsa is the private key i used in the master image. This master image also includes the Eclipse Theia which is a browser based IDE. The IDE can be accessed on port 8000 after the master container is launched.


The ansible-target-node dockerfile can be used to create a centos7 ansible target node images , As we are working on a container, we’ll need to install initscripts and openssh-server-sysvinit, as systemctl doesn’t work here. The bootstrap script will start the sshd service during the container startup and the public key of the user ansible is included in the target image. 

The docker-compose.yml can be used to launch a working ansible environment for local development or learning purpose, This launches a control node and 4 target nodes (1 load balancer,2 application node and 1 database nodes). You can able to access all the target nodes from the control nodes via SSH and.
