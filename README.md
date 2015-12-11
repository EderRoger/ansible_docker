# ansible_docker
A simple example using module ansible docker to build an container enviroment

# Start a environment 

``$ vagrant up``

# Runing  playbook install tag

``$ ansible-playbook -i staging --tags "install" -u vagrant webserver.yml -vvvv``


# Runing  playbook container task

``$ ansible-playbook -i staging --tags "copy_file,image,container_nginx" -u vagrant webserver.yml -vvvv``

# Test NGinx home page

`` Your web browser http://192.168.33.15:32768``
