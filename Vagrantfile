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
      # ansible.start_at_task = "create intershop user"
    end
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8196"
  end
end
