# -*- mode: ruby -*-
# vim: set ft=ruby ts=2 sw=2 expandtab:

Vagrant.configure(2) do |config|
  config.vm.box = "boxcutter/centos66"

  # sislegis4 - Wildfly master, HAProxy  
  config.vm.define "sislegis4" do |sislegis4|
    sislegis4.vm.hostname="sislegis4"
    sislegis4.vm.network "private_network", ip: "172.17.6.84"
    sislegis4.vm.network :forwarded_port, guest: 9990, host: 9990
    sislegis4.vm.network :forwarded_port, guest: 80, host: 8080
    sislegis4.vm.provision "shell", path: "sislegis4/instalar", privileged: false
  end

  # sislegis1 - Wildfly slave1
  config.vm.define "sislegis1" do |sislegis1|
    sislegis1.vm.hostname="sislegis1"
    sislegis1.vm.network "private_network", ip: "172.17.6.81"
    sislegis1.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    sislegis1.vm.provision "shell" do |s|
      s.path = "sislegis1/instalar"
      s.args = "sislegis1"
      s.privileged = false
    end
  end

  # sislegis2 - Wildfly slave2
  config.vm.define "sislegis2" do |sislegis2|
    sislegis2.vm.hostname="sislegis2"
    sislegis2.vm.network "private_network", ip: "172.17.6.82"
    sislegis2.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    sislegis2.vm.provision "shell" do |s|
      s.path = "sislegis2/instalar"
      s.args = "sislegis2"
      s.privileged = false
    end
  end

  # sislegis3 - Wildfly keycloak, postgresql
  config.vm.define "sislegis3" do |sislegis3|
    sislegis3.vm.hostname="sislegis3"
    sislegis3.vm.network "private_network", ip: "172.17.6.83"
    sislegis3.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    sislegis3.vm.provision "shell" do |s|
      s.path = "sislegis3/instalar"
      s.privileged = false
    end
  end
end
