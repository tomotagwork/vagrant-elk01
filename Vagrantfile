# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  ## Virtual Machine Setting
  #
  config.vm.box = "ubuntu/xenial64"
  config.vm.hostname = 'elk01'
  config.vm.network :private_network,ip: "192.168.10.10"
  config.vm.network :forwarded_port, guest: 9200, host: 19200
  config.vm.network :forwarded_port, guest: 5601, host: 15601
  config.vm.provider "virtualbox" do |vbox|
    vbox.name = "vagrant-elk01"
    vbox.gui = false        
    vbox.cpus = 4
    vbox.memory = 4096
  end

  ## Ansible
  #
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook       = "elk01.yml"
    ansible.version        = "latest"      
    ansible.verbose        = false
    ansible.install        = true
    ansible.limit          = "elk01"      
    ansible.inventory_path = "hosts"
  end
end
