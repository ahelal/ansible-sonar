# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_BASE_PORT = "99"
VAGRANT_SSH_PORT = "22" + VAGRANT_BASE_PORT
VAGRANT_NETWORK_IP = "192.168.11." + VAGRANT_BASE_PORT

Vagrant.configure("2") do |config|

  # required to download the box if used for the first time
  # vagrant box add ubuntu14 https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-i386-vagrant-disk1.box
  config.vm.box = "ubuntu_trusty_x64"

  config.vm.define :master do |master|
    #master.vm.network :private_network, ip: VAGRANT_NETWORK_IP
    master.vm.provider :virtualbox do |vb|
      vb.name = "sonar"
      vb.customize ["modifyvm", :id, "--memory", "4096"]
    end
	master.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
	master.vm.network "forwarded_port", guest: 22, host: VAGRANT_SSH_PORT, auto_correct: true
	master.vm.network "forwarded_port", guest: 9000, host: 9000, auto_correct: true
	master.vm.network "forwarded_port", guest: 3306, host: 3306, auto_correct: true
  end

end
