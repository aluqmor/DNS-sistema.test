# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
    config.vbguest.auto_update = false
  
    # Máquina imaginaria Mercurio 192.168.57.101
    
    config.vm.define "venus" do |venus|
      venus.vm.box = "debian/bookworm64" 
      venus.vm.hostname = "venus.sistema.test"
      venus.vm.network "private_network", ip: "192.168.57.102"
      venus.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y bind9 dnsutils
      SHELL
    end
    
    config.vm.define "tierra" do |tierra|
      tierra.vm.box = "debian/bookworm64"
      tierra.vm.hostname = "tierra.sistema.test"
      tierra.vm.network "private_network", ip: "192.168.57.103"
      tierra.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y bind9 dnsutils
      SHELL
    end
    
    # Máquina imaginaria Marte 192.168.57.104

end
