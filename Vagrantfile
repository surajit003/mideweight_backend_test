# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 9099, host: 9099
  config.vm.network "forwarded_port", guest: 5356, host: 5356
  config.vm.synced_folder ".", "/vagrant-test"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 4
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y python3-pip redis
    sudo pip3 install -r /vagrant-test/requirements.txt
  SHELL
end
