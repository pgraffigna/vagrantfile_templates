# -*- mode: ruby -*-
# vi: set ft=ruby :

imagen = "geerlingguy/debian10"

$script = <<-SCRIPT
sudo apt-get update
sudo apt-get install -y task-xfce-desktop
SCRIPT

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.define "master" do |m|
    m.vm.box = imagen
    m.vm.network "public_network"
    m.vm.hostname = "master"

    m.vm.provider :virtualbox do |vb|
      vb.name = "template"
      vb.memory = 2048
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--vram", "12"]
      vb.check_guest_additions = false
    end

    config.vm.provision "shell", inline: $script
  end  
end
