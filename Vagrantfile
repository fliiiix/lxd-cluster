# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "ansible/playbook.yaml"
  end
  
  config.vm.define "server1" do |server1|
    server1.vm.hostname = "server1"
    server1.vm.network "private_network", ip: "192.168.10.10", virtualbox__intnet: "lxdcluster"
  end

  config.vm.define "server2" do |server2|
    server2.vm.hostname = "server2"
    server2.vm.network "private_network", ip: "192.168.10.11", virtualbox__intnet: "lxdcluster"
  end

  config.vm.define "server3" do |server3|
    server3.vm.hostname = "server3"
    server3.vm.network "private_network", ip: "192.168.10.12", virtualbox__intnet: "lxdcluster"
  end

  # Increase memory for Virtualbox
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end
end
