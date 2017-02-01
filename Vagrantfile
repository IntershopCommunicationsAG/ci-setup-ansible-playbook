# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/centos7"
  config.vm.define "ciserver", autostart: false do |ciserver|
    ciserver.vm.hostname = "ciserver"
    ciserver.vm.network "forwarded_port", guest: 8081, host: 18081
    ciserver.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "setupci.yml"
      # ansible.verbose = "-v"
      # ansible.start_at_task = "download responsive starter store"
    end
  end

  config.vm.define "devvm", primary: true do |devvm|
    spsdev.vm.hostname = "devvm"
    spsdev.vm.network "forwarded_port", guest: 80, host: 10080
    spsdev.vm.network "forwarded_port", guest: 443, host: 10443
    spsdev.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "devvm.yml"
      # ansible.verbose = "-vvv"
    end
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8196"
  end
end
