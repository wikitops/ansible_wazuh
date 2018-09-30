# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  # Wazuh Server
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "wazuh-server0#{i}" do |server|
      server.vm.hostname = "wazuh-server0#{i}"
      server.vm.network "private_network", ip: "10.0.4.18#{i}"
    end
  end

  # Wazuh Agent
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "wazuh-agent0#{i}" do |server|
      server.vm.hostname = "wazuh-agent0#{i}"
      server.vm.network "private_network", ip: "10.0.4.19#{i}"
    end
  end

  # Provision
  config.vm.provision "shell", path: "provision.sh"
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/authorized_keys"

end
