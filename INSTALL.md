Perform apt setup according to
https://docs.docker.com/engine/installation/linux/ubuntulinux/
check apt cache
> apt-cache madison docker-engine

Instead of latest version install
sudo apt-get install docker-engine=1.11.2-0~xenial

Modify docker daemon start options and start:
> sudo vim /lib/systemd/system/docker.service
ExecStart=/usr/bin/docker daemon -H tcp://127.0.0.1:80 -H unix:///var/run/docker.sock
> systemctl daemon-reload
> sudo service docker start

If docker daemon fails to start try:
sudo rm /var/lib/docker/network/files/local-kv.db


git clone https://github.com/lavacat/glot-run.git

Install eglang https://www.erlang-solutions.com/resources/download.html

wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb
sudo dpkg -i erlang-solutions_1.0_all.deb
sudo apt-get update
sudo apt-get install erlang

install rebar3
https://www.rebar3.org/docs/getting-started

build release:
> ./make_release.sh

export vars from devel.sh
run glot
> glot/bin/glot start



curl -X GET 'http://162.243.140.222:8090/languages'


curl --request POST \
     --header 'Authorization: Token clumeterin' \
     --header 'Content-type: application/json' \
     --data '{"token": "d11088bc-a29d-4d49-a633-b1b1ae807064"}' \
     --url 'http://162.243.140.222:8090/admin/users'


curl --request PUT \
     --header 'Authorization: Token clumeterin' \
     --header 'Content-type: application/json' \
     --data '{"name": "python", "version": "latest", "image": "glot/python:latest"}' \
     --url 'http://162.243.140.222:8090/admin/languages'

curl -v --request POST \
     --header 'Authorization: Token d11088bc-a29d-4d49-a633-b1b1ae807064' \
     --header 'Content-type: application/json' \
     --data '{"files": [{"name": "main.py", "content": "print(42)"}]}' \
     --url 'http://162.243.140.222:8090/languages/python/latest'