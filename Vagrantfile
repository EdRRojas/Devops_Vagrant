# Vagrantfile
Vagrant.configure("2") do |config|
    # Usar Ubuntu 22.04 como sistema operativo base
    config.vm.box = "ubuntu/jammy64"
  
    config.vm.hostname = "DevopsVagrantServer"

    # Configuración de la máquina virtual
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Asignar una IP privada para acceder a Apache
    config.vm.network "private_network", ip: "192.168.56.10"
  
    # Compartir la carpeta local con el directorio web de Apache
    config.vm.synced_folder "src", "/var/www/html"
  
    # Configuración para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      # Actualizar repositorios e instalar Apache
      sudo apt-get update
      sudo apt-get install -y apache2
      # Permitir que todos los usuarios puedan editar el contenido de /var/www/html
      sudo chown -R vagrant:vagrant /var/www/html
    SHELL
  end
  