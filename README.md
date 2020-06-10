# ansible

The ansible-master dockerfile can be used to create a centos7 master image with a user named ansible, please generate a key-pair and add the private key into this image. This is required since the master needs to have passwordless SSH access to all the target nodes. Here id_rsa is the private key i used in the master image.
