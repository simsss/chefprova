# encoding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.define "jenkins" do |cs|
    cs.vm.box = "bento/centos-7.2"  
    cs.vm.hostname = "jenkins"
    cs.vm.network "forwarded_port", guest: 80, host: 8082
    cs.vm.network "public_network", bridge: "en0: Ethernet", mode: "DHCP"



    cs.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end
  
cs.vm.provision :chef_zero do |chef|
      chef.roles_path = './chef/roles'
      chef.data_bags_path = './chef/data_bags'
      chef.nodes_path = './chef/nodes'
      chef.environments_path = './chef/environments'
      chef.cookbooks_path = './chef/cookbooks'

     # chef.run_list = [
     #  "role[my_jenkins]"
     # ]
	
	chef.add_recipe "jenkins::default"
  end
  end


config.vm.define "artifactory" do |n|
    n.vm.box = "bento/centos-7.2"
    n.vm.hostname = "artifactory"
    n.vm.network "forwarded_port", guest: 80, host: 8081
    n.vm.network "public_network", bridge: "en0: Ethernet", mode: "DHCP"



    n.vm.provider "virtualbox" do |w|
w.cpus = 1
w.memory =2048
    end


      n.vm.provision :chef_zero do |chef|
      chef.roles_path = './chef/roles'
      chef.data_bags_path = './chef/data_bags'
      chef.nodes_path = './chef/nodes'
      chef.environments_path = './chef/environments'
      chef.cookbooks_path = './chef/cookbooks'

     # chef.run_list = [
     #  "role[my_artifactory]"
     # ]
	chef.add_recipe "artifactory::default"
  end
end
end


