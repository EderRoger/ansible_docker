# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ansible_docker"
  config.vm.box_url =  "https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box"

  ssh_public_key = File.read(File.join(Dir.home, ".ssh", "id_rsa.pub"))

  config.vm.define :webapp do |web_config|
    web_config.vm.network :private_network, :ip => "192.168.33.15"
    web_config.vm.host_name = "nginx"

    web_config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      echo "#{ssh_public_key}" >> /home/vagrant/.ssh/authorized_keys
    SHELL

    web_config.vm.provision :ansible do |ansible|
      ansible.playbook = "webserver.yml"
      ansible.verbose = "vvv"
    end
  end
end

