# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true
  
  config.vm.define "template" do |t|
    t.vm.box = "geerlingguy/ubuntu2004"
    t.vm.network "private_network", ip: "192.168.60.10"
    t.vm.hostname = "template"

    t.vm.provider :virtualbox do |v|
      v.name = "template"
      v.memory = 512
      v.cpus = 1
      v.check_guest_additions = false
    end
  end
end