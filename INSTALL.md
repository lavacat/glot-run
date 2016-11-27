https://docs.docker.com/engine/installation/linux/ubuntulinux/

/etc/default/docker
DOCKER_OPTS="-H tcp://172.17.0.1:80 -H unix:///var/run/docker.sock"