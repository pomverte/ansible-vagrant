# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.3"

  config.vm.define "vm-vangrant-node-1" do |node1|
    node1.vm.synced_folder '.', '/vagrant', disabled: true
    node1.vm.network "private_network", ip: "172.17.177.21"
    node1.vm.provider "virtualbox" do |vb|
      vb.name = "vm-vangrant-node-1"
    end
  end
  config.vm.define "vm-vangrant-node-2" do |node2|
    node2.vm.synced_folder '.', '/vagrant', disabled: true
    node2.vm.network "private_network", ip: "172.17.177.22"
    node2.vm.provider "virtualbox" do |vb|
      vb.name = "vm-vangrant-node-2"
    end
  end

  config.vm.define 'controller', primary: true do |machine|
    machine.vm.network "private_network", ip: "172.17.177.11"

    machine.vm.provider "virtualbox" do |vb|
      vb.name = "vm-vangrant-ansible"
    end

    machine.vm.provision :ansible_local do |ansible|
      ansible.version = "2.3.1.0"
      ansible.verbose = "vv"
      ansible.provisioning_path = "/vagrant/provisioning"
      ansible.playbook = "playbook.yml"
      ansible.inventory_path = "inventory.yml"
    end
  end

end
