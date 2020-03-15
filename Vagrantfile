Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 80, host: 9091
  config.vm.network "forwarded_port", guest: 80, host: 5000
  config.vm.network "public_network", ip: "192.168.1.24"
  
  config.vm.define "dockerhost" do |dockerhost|
        dockerhost.vm.provider "virtualbox" do |vb|
            vb.name = "ubuntu_dockerhost"
        end
		end

        
    
  
  config.vm.provision "shell",
    inline: "cat /configs/id_bionic.pub >> .ssh/authorized_keys"
	#config.vm.provision "shell",
    #inline: inline: "apt-get update && apt-get install -y docker.io"
   config.vm.provision "shell",
   inline: "apt-get update && apt-get install -y docker.io && apt-get install git&& git clone https://github.com/dockersamples/docker-pets.git&& cd docker-pets/web&& docker build -t docker-pets . && docker run -it -p 5000:5000 docker-pets"
    #inline: "apt-get install git&& git clone https://github.com/dockersamples/docker-pets.git&& cd docker-pets/web&& docker run -it -p 5000:5000 docker-pets"
   
  config.vm.synced_folder "./configs", "/configs"
  config.vm.synced_folder ".", "/vagrant", disabled: true
end
