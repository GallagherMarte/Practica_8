# Vagrantfile for setting up Apache web server with a shared folder
Vagrant.configure("2") do |config|
  
    # Base box
    config.vm.box = "ubuntu/bionic64"

      # Asignar un nombre de host para la máquina virtual
  config.vm.hostname = "webServer"
  
    # Set machine details
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Set up hostname
    config.vm.hostname = "apache-server"
  
    # Network settings
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Sync local directory to the Apache web server directory
    config.vm.synced_folder "src", "/var/www/html", type: "virtualbox"
  
    # Provision Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  
  end
  