Vagrant.configure("2") do |config|
  # Usar una imagen de Ubuntu (puedes cambiarla si prefieres otra)
  config.vm.box = "ubuntu/bionic64"

  # Configurar la memoria y CPU
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end

  # Configurar red privada con una IP estática
  config.vm.network "private_network", type: "static", ip: "192.168.56.10"

  # Compartir la carpeta de apache con una carpeta local
  config.vm.synced_folder "./web", "/var/www/html"

  # Provisionar con Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo systemctl enable apache2
    echo "<h1>Hola Mundo desde Apache en Vagrant</h1>" > /var/www/html/index.html
  SHELL
end