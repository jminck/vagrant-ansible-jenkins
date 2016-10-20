# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
#  config.vm.box_url = "https://github.com/kraksoft/vagrant-box-ubuntu/releases/download/14.04/ubuntu-14.04-amd64.box"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "jenkins-dev.yml"
    ansible.sudo = true
    ansible.extra_vars = "ansible-settings.yml"
  end
  config.vm.synced_folder ".", "/vagrant"
  config.vm.network "private_network", ip: "10.0.0.105"
  config.vm.network "forwarded_port", host: 8888, guest: 8080
  config.vm.provider "virtualbox" do |v|
    v.name = "Jenkins VM"
  end
end
