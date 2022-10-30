# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.define "windows10" do |win10|
    win10.vm.box = "gusztavvargadr/windows-10"
    win10.vm.network "private_network", ip: "10.0.0.10"
    win10.vm.boot_timeout = 300 # 5 minutes
  end
  config.vm.boot_timeout = 300
  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu/focal64"
    ubuntu.vm.network "private_network", ip: "10.0.0.20"
    ubuntu.vm.provider "virtualbox" do |vbubuntu|
      vbubuntu.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
      vbubuntu.cpus = 1
      vbubuntu.memory = "512"
    end
    ubuntu.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get upgrade
      sudo apt install apache2
    SHELL
  end
  config.vm.boot_timeout = 300
  config.vm.define "centos" do |centos|
    centos.vm.box = "centos/8"
    centos.vm.network "private_network", ip: "10.0.0.30"
    centos.vm.provider "virtualbox" do |vbcentos|
      vbcentos.cpus = 1
      vbcentos.memory = "1024"
    end
  end
end