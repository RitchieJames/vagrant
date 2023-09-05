# -*- mode: ruby -*-
# vi: set ft=ruby :

# Define the VM properties
VM1 = {
  box: "centos/7",
  hostname: "app1",
  memory: 1024,
  cpus: 1
}

VM2 = {
  box: "centos/7",
  hostname: "app2",
  memory: 1024,
  cpus: 1
}

Vagrant.configure("2") do |config|
  config.vm.define VM1[:hostname] do |vm_config|
    vm_config.vm.box = "ubuntu/trusty64"
    vm_config.vm.hostname = VM1[:hostname]
    vm_config.vm.network "private_network", ip: "192.168.100.3"
    vm_config.vm.provider "virtualbox" do |vb| 
      vb.name = VM1[:hostname]
      vb.memory = VM1[:memory]
      vb.cpus = VM1[:cpus]
      

    end
  end
  config.vm.define VM2[:hostname] do |vm_config|
    vm_config.vm.box = "ubuntu/trusty64"
    vm_config.vm.hostname = VM2[:hostname]
    vm_config.vm.network "private_network", ip: "192.168.100.4"
    vm_config.vm.provider "virtualbox" do |vb|
      vb.name = VM2[:hostname]
      vb.memory = VM2[:memory]
      vb.cpus = VM2[:cpus]
    end
  end
 
end

