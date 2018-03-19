# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant setup for minecraft servers. For use with virtualbox

$BRIDGE_DEVICE = 'en0: Wi-Fi (AirPort)'

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.provision :shell, :path => "minecraft_bootstrap"

    config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install apache2 -y
    sudo apt-get install ufw -y
    sudo ufw allow from * to any port 22
    sudo ufw allow from * to any port 25565
    sudo ufw allow 80/tcp
    sudo ufw --force enable
    sudo apt-get install libapache2-mod-proxy-html -y
    sudo apt-get install libxml2-dev -y
    a2enmod proxy
    a2enmod proxy_html
    a2enmod proxy_http
    sed -i '$aServerName localhost' /etc/apache2/apache2.conf
    service apache2 restart
    cd /etc/apache2/sites-enabled
    wget https://pastebin.com/raw/GbjFC2ii
    cp GbjFC2ii 001-reverseproxy.conf
  SHELL

  
  config.vm.provider "virtualbox" do |v|
    v.memory = 1536
  end

  config.vm.network "forwarded_port", guest: 25565, host: 25565


  config.vm.hostname = "minecraft.local"
end
