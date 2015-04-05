# -*- mode: ruby -*-
# vim: set ft=ruby ts=2 sw=2 expandtab:

Vagrant.configure(2) do |config|
  config.vm.box = "boxcutter/centos66"
  
  config.vm.define "master" do |master|
    master.vm.hostname="sislegis4"
    master.vm.network "private_network", ip: "172.17.6.84"
    master.vm.network :forwarded_port, guest: 9990, host: 9990
    master.vm.network :forwarded_port, guest: 80, host: 8080
    master.vm.provider "virtualbox" do |v|
      v.memory = 512
    end
    master.vm.provision "shell", path: "master/instalar", privileged: false
  end

  config.vm.define "slave1" do |slave1|
    slave1.vm.hostname="sislegis1"
    slave1.vm.network "private_network", ip: "172.17.6.81"
    #slave1.vm.network :forwarded_port, guest: 8080, host: 8180
    slave1.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    slave1.vm.provision "shell" do |s|
      s.path = "slave1/instalar"
      s.args = "slave1"
      s.privileged = false
    end
  end

  config.vm.define "slave2" do |slave2|
    slave2.vm.hostname="sislegis2"
    slave2.vm.network "private_network", ip: "172.17.6.82"
    #slave2.vm.network :forwarded_port, guest: 8080, host: 8280
    slave2.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    slave2.vm.provision "shell" do |s|
      s.path = "slave2/instalar"
      s.args = "slave2"
      s.privileged = false
    end
  end

=begin
  config.vm.define "postgres" do |postgres|
    postgres.vm.hostname="sislegis3"
    postgres.vm.network "private_network", ip: "172.17.6.83"
  end
=end
end
