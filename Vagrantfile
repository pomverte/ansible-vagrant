# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.3"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "vm-vangrant-ansible"
  end

  config.vm.provision :ansible_local do |ansible|
    ansible.version = "2.3.1.0"
    ansible.verbose = "vv"
    ansible.provisioning_path = "/vagrant/provisioning"
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "inventory.yml"
  end

end
