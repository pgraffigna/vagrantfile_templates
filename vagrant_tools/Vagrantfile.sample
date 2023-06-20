ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
IMAGEN = "generic/ubuntu2004"

$script = <<-SCRIPT
sudo apt-get update
sudo apt-get install -y task-xfce-desktop
SCRIPT

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", type: "rsync"
 
  config.vm.define :server do |s|
    s.vm.box = IMAGEN
    s.vm.hostname = "ansible-test"
    s.vm.box_check_update = false
    s.vm.provision :docker
    s.vm.provision :docker_compose    

    s.vm.network "forwarded_port", guest: 80, host: 8080

    s.vm.provision "shell", inline: $script 

    s.vm.provider :libvirt do |v|
      v.memory = 1024  
      v.cpus = 2
    end
  end  
end
