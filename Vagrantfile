# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # Seleccionar la box que usaremos
    config.vm.box = "ubuntu/bionic64"  # Usando Ubuntu 18.04 como base
  
    # Configurar recursos de la VM
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Configurar red privada para acceder al servidor web
    config.vm.network "private_network", ip: "192.168.56.10"
  
    # Compartir directorio entre la VM y el host
    config.vm.synced_folder ".", "/var/www/html"  # Sincroniza el directorio actual con el de Apache
  
    # Provisión para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
    SHELL
  end
  