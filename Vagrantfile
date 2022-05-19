# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

HOSTNAME = "sonar"
VAGRANT_BASE_PORT = "99"
VAGRANT_SSH_PORT = "22" + VAGRANT_BASE_PORT
VAGRANT_NETWORK_IP = "192.168.11." + VAGRANT_BASE_PORT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # required to download the box if used for the first time
  # vagrant box add ubuntu14 https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-i386-vagrant-disk1.box
  config.vm.box = "ubuntu_trusty_x64"

  config.vm.define :sonar do |vagrant|
    vagrant.vm.hostname = HOSTNAME
    vagrant.vm.network :private_network, ip: VAGRANT_NETWORK_IP
    vagrant.vm.provider :virtualbox do |vb|
      vb.name = "sonar"
      vb.customize ["modifyvm", :id, "--memory", "4096"]
    end
	vagrant.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh", disabled: "true"
	vagrant.vm.network "forwarded_port", guest: 22, host: VAGRANT_SSH_PORT, auto_correct: true
	vagrant.vm.network "forwarded_port", guest: 9000, host: 9000, auto_correct: true
	vagrant.vm.network "forwarded_port", guest: 3306, host: 3306, auto_correct: true
  end

end
