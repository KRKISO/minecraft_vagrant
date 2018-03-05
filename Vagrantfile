# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant setup for minecraft servers. For use with virtualbox

$BRIDGE_DEVICE = 'en0: Wi-Fi (AirPort)'

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.provision :shell, :path => "minecraft_bootstrap"


  config.vm.provider "virtualbox" do |v|
    v.memory = 1536
  end

  config.vm.network "forwarded_port", guest: 25565, host: 25565


  config.vm.hostname = "minecraft.local"
end
