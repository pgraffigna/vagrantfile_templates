# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true
    
  unless Vagrant.has_plugin?("vagrant-vbguest")
    puts 'Instalando el plugin vagrant-vbguest ...'
    system('vagrant plugin install vagrant-vbguest')
  end

  unless Vagrant.has_plugin?("vagrant-docker-compose")
    puts 'Instalando el plugin vagrant-docker-compose ...'
    system('vagrant plugin install vagrant-docker-compose')
  end

  config.vm.define "master" do |m|
    m.vm.box = "geerlingguy/ubuntu1804"
    m.vm.network "private_network", ip: "192.168.60.10"
    m.vm.hostname = "master"
    
    m.vm.provision "shell", 
    inline: "sudo echo 192.168.60.11 node | sudo tee -a /etc/hosts"
    
    m.vm.provider :virtualbox do |vb|
      v.name = "template"
      v.memory = 512
      v.cpus = 1
      v.check_guest_additions = false 
    end 
  end  
    
  config.vm.define "node" do |n|
    n.vm.box = "geerlingguy/ubuntu1804"
    n.vm.network "private_network", ip: "192.168.60.11"
    n.vm.hostname = "node"
    
    n.vm.provision "shell",
    inline: "sudo echo 192.168.60.10 master | sudo tee -a /etc/hosts"
  end  
end
