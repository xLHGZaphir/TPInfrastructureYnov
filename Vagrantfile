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
        curl -L "https://github.com/docker/compose/releases/download/1.25.0/docker-compose-$(uname$
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

  config.vm.define "freenas" do |freenas|
    freenas.vm.box = "robuyo/freenas112"
    freenas.vm.box_version = "1"
   # freenas.vm.hostname = "freenas"
   freenas.vm.network "public_network", bridge: "en0"
    freenas.vm.provision "shell", inline: <<-SHELL
    yum update -y
    SHELL
 # end
    freenas.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = "2048"
    end
  end

end

