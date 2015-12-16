# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ansible_docker"
  config.vm.box_url =  "https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box"

  ssh_public_key = File.read(File.join(Dir.home, ".ssh", "id_rsa.pub"))

  (1..2).each do |i|
    config.vm.define "web_#{i}" do |web_config|
      web_config.vm.network :private_network, :ip => "192.168.33.1#{i}"
      web_config.vm.host_name = "web#{i}"

      web_config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      echo "#{ssh_public_key}" >> /home/vagrant/.ssh/authorized_keys
      SHELL
    end
  end

  config.vm.define :lb do |web_config|
    web_config.vm.network :private_network, :ip => "192.168.33.19"
    web_config.vm.host_name = "lb"

    web_config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      echo "#{ssh_public_key}" >> /home/vagrant/.ssh/authorized_keys
    SHELL
#    web_config.vm.provision :ansible do |ansible|
#      ansible.playbook = "webserver.yml"
#      ansible.verbose = "vvv"
#    end
  end
end

