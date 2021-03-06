# -*- mode: ruby -*-
# vim: set ft=ruby ts=2 sw=2 expandtab:

Vagrant.configure(2) do |config|

  # ajusta do default provider para o virtualbox
  ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

  # Todas as VMs são baseadas no CentOS 6.6
  config.vm.box = "boxcutter/centos66"

  # sislegis3 - construída primeiro para disponibilizar os seguintes serviços:
  #
  # 1) postgresql: banco utilizado pelo sislegis
  # 2) keycloak: http://keycloak.mj.gov.br
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

  # sislegis4 - balanceador de carga (HAProxy) e controlador do domínio (master)
  #
  # HAProxy - http://sislegis.mj.gov.br
  # Wildfly master - http://sislegis.mj.gov.br:9990
  config.vm.define "sislegis4" do |sislegis4|
    sislegis4.vm.hostname="sislegis4"
    sislegis4.vm.network "private_network", ip: "172.17.6.84"
    sislegis4.vm.provision "shell", path: "sislegis4/instalar", privileged: false
  end

  # sislegis1 - Wildfly slave 1
  config.vm.define "sislegis1" do |sislegis1|
    sislegis1.vm.hostname="sislegis1"
    sislegis1.vm.network "private_network", ip: "172.17.6.81"
    sislegis1.vm.provision "shell", path: "sislegis1/instalar", privileged: false
    sislegis1.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
  end

  # sislegis2 - Wildfly slave 2
  config.vm.define "sislegis2" do |sislegis2|
    sislegis2.vm.hostname="sislegis2"
    sislegis2.vm.network "private_network", ip: "172.17.6.82"
    sislegis2.vm.provision "shell", path: "sislegis2/instalar", privileged: false
    sislegis2.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
  end

end
