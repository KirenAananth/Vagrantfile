# -*- mode: ruby -*-
# vi: set ft=ruby :

# Configuring the Software , Hardware & Network

Vagrant.configure("2") do |config|
config.vm.box = "centos/7"
config.vm.provider :virtualbox do |vb| 
vb.name = "test-vag1" 
vb.memory = 512 
vb.cpus = 2
end 
  config.vm.network "public_network" , bridge: "Hyper-V Virtual Ethernet Adapter #4"

# Executing script to Allow root & passwd Authenication.
  
$script = <<-SCRIPT
sudo sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/g' /etc/ssh/sshd_config
sudo sed -i 's/PasswordAuthentication no/#PasswordAuthentication no/g' /etc/ssh/sshd_config
sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/g' /etc/ssh/sshd_config
`sudo systemctl restart sshd`
sudo hostnamectl set-hostname test-vag1.local.com
SCRIPT
  config.vm.provision "shell", inline: $script
  
# SSH default login 
# username = vagrant , passwd = vagrant

# NETWORKING
# change the bridged adapter name based on your computer.

# Important commands
#vagrant init centos/7 #To initialize vagrant for 1st time.
#vagrant up #To start the machine for the 1st time/after destroy.
#vagrant destroy #To remove the machine.
#vagrant box remove #To completely remove the box.
#vagrant ssh-config #To check the ssh configurations.
#vagrant ssh #To ssh directly into the VM from shell.
#vagrant suspend #To save the machine in current state.
#vagrant resume #To start the machine from the saved state.
#vagrant halt #To gracefully shutdown VM.
#vagrant reload #To resatrt the VM.

# Disable automatic box update checking. If you disable this, then
# boxes will only be checked for updates when the user runs
# `vagrant box outdated`. This is not recommended.
config.vm.box_check_update = false

# config.vm.provider "virtualbox" do |vb|
# # Display the VirtualBox GUI when booting the machine
# vb.gui = true

end
