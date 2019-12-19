# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.synced_folder "./", "/vagrant"

#  config.vm.provision "shell", inline: <<-SHELL
#    yum update -y
#    yum upgrade -y
#  SHELL

  config.vm.define "netbox" do |netbox|
    netbox.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "2048"
   # end
    netbox.vm.hostname =  "netbox"
    netbox.vm.network "private_network", ip: "10.1.1.2"
    netbox.vm.provision "shell", inline: <<-SHELL
	yum install -y vim git
	yum install -y install dnf-plugins-core yum-utils
	yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
	#yum-config-manager --set-disabled docker-ce-nightly
	yum -y install docker-ce
	curl -L "https://github.com/docker/compose/releases/download/1.25.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
        chmod +x /usr/local/bin/docker-compose
	sudo systemctl enable --now docker
	docker pull netboxcommunity/netbox
	git clone -b master https://github.com/netbox-community/netbox-docker.git
	cd netbox-docker
	firewall-cmd --add-port=8080/tcp --permanent
	firewall-cmd --reload
	/usr/local/bin/docker-compose pull
	/usr/local/bin/docker-compose up -d
    SHELL
  end
end

  config.vm.define "machine1" do |machine1|
    machine1.vm.box = "centos/7"
    machine1.vm.box_version = "1905.1"
    machine1.vm.network "public_network", bridge: "en0"
    machine1.vm.provision "shell", inline: <<-SHELL
    yum update -y
    yum install -y ansible
    SHELL
   #config.vm.provision "ansible" do |ansible|
   #machine1.playbook = "centos7-update.yml"
    end
#end
#  config.vm.define "machine2" do |machine2|
#    machine2.vm.box = "Microsoft/EdgeOnWindows10"
#    machine2.vm.box_version = "1.0"
#    config.vm.provision "ansible" do |ansible|
#    machine2.playbook = "W7-update.yml"
#    machine2.vm.network "public_network", bridge: "en0"
#    machine2.vm.provider "virtualbox" do |vb|
#      vb.gui = false
#      vb.memory = "2048"
#    end
#end

   config.vm.define "glpi" do |glpi|
    glpi.vm.box = "adurand16000/GLPI-9.4.4"
    glpi.vm.box_version = "9.4.4.1"
    glpi.vm.network "public_network", bridge: "en0"
    glpi.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "2048"
    end
end

 config.vm.define "freenas" do |freenas|
    freenas.vm.box = "robuyo/freenas112"
    freenas.vm.box_version = "1"
    freenas.vm.network "public_network", bridge: "en0"
    freenas.vm.provision "shell", inline: <<-SHELL
    yum update -y
    yum install -y ansible
    SHELL
    #config.vm.provision "ansible" do |ansible|
    #ansible.playbook = "update-freenas.yml"
    freenas.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "2048"
    end
end 
end

