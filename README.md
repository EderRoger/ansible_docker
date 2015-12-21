# Ansible, Docker provisioning a HAProxy Loadbalancing

A simple example using module ansible docker to build an container enviroment

# Start a environment

``$ vagrant up``

# Run  playbook - install

``$ ansible-playbook -i staging --tags "install" -u vagrant webserver.yml -vvvv``

# Run  playbook -  docker

``$ ansible-playbook -i staging --tags "docker" -u vagrant webserver.yml -vvvv``

# Run  playbook - install lb

``$ ansible-playbook -i lb --tags "install" -u vagrant webserver.yml -vvvv``


# Test HAProxy home page

`` Your web browser http://192.168.33.19``

# HAProxy status page

`` Your web browser http://192.168.33.19/haproxy?stats``

# Run apache benchmark

`` ab -c 40 -n 10000 http://192.168.33.19/ ``


# See your container status

``$ vagrant ssh -c web_1 "docker ps"``


