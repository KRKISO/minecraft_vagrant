$BRIDGE_DEVICE = 'en0: Wi-Fi (AirPort)'
Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.provision "shell", path: => "minecraft_bootstrap"
  config.vm.provider "virtualbox" do |vb|
  vb.memory = 1024
  end
  config.vm.network "forwarded_port", guest: 25565, host: 25565
  config.vm.hostname = "minecraft.local"
end
  config.vm.provision "shell", inline: <<-SHELL 
    apt-get install screen -y
	cd /opt/minecraft
	java -jar minecraft_server.1.8.jar
  SHELL
end
