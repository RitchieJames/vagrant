# -*- mode: ruby -*-
# vi: set ft=ruby :
#This script will create two vm's named "ansible-cnt" and "ansible-client"
#This script uses centos/7 vagrant box 
#This script require creation of Hostonly adaptor in the virtual machine as a prerequisite
#This script require ip of the hostonly adaptor in the OS to be set as 192.168.100.x
#This script will install ansible 
# Define the VM properties
VM1 = {
  box: "geerlingguy/rockylinux8",
  hostname: "ansible-client",
  memory: 1024,
  cpus: 1
}

VM2 = {
  box: "geerlingguy/rockylinux8",
  hostname: "ansible-controller",
  memory: 1024,
  cpus: 1
}

Vagrant.configure("2") do |config|
  config.vm.define VM1[:hostname] do |vm_config|
    vm_config.vm.box = VM1[:box]

  
    vm_config.vm.hostname = VM1[:hostname]
    vm_config.vm.network "private_network", ip: "192.168.100.4"
    vm_config.vm.provider "virtualbox" do |vb| 
      vb.name = VM1[:hostname]
      vb.memory = VM1[:memory]
      vb.cpus = VM1[:cpus]
      

    end
  end
  config.vm.define VM2[:hostname] do |vm_config|
    vm_config.vm.box = VM2[:box]
#Shell commands after vm creation

    vm_config.vm.provision "shell" , inline: <<-SHELL
      sudo yum install epel-release -y
      sudo yum install ansible -y
      sudo ssh-keygen
      ssh-keygen -t rsa -N "" -f ~/.ssh/mykey
      sshpass -p "vagrant" ssh-copy-id -i ~/.ssh/mykey.pub vagrant@192.168.100.4

    SHELL
    vm_config.vm.hostname = VM2[:hostname]   
    vm_config.vm.network "private_network", ip: "192.168.100.3"
    vm_config.vm.provider "virtualbox" do |vb|
      vb.name = VM2[:hostname]
      vb.memory = VM2[:memory]
      vb.cpus = VM2[:cpus]
    end
  end
 
end

