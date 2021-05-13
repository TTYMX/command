# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.require_version ">= 1.6.0"

boxes = [
    {
      :name => "vagrant1",
      :eth1 => "192.168.1.10",
      :memory => "1024",
      :cpu => 1
    },
    {
      :name => "vagrant2",
      :eth1 => "192.168.1.11",
      :memory => "1024",
      :cpu => 1
    }
]
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  # config.vm.box = "centos/7"
  # Disable grant1" do |vb|
  
  config.vm.box = "centos/7"

  boxes.each do |box|
    config.vm.define box[:name] do |config|
        config.vm.hostname = box[:name]
        config.vm.network :public_network, ip: box[:eth1]
        # config.vagrant.plugins = ["vagrant-vbguest"]

        config.vm.provider "virtualbox" do |vb|
            vb.customize ["modifyvm", :id, "--cpus", box[:cpu]]
            vb.customize ["modifyvm", :id, "--memory", box[:memory]]
        end

        config.vm.provider "vmware_fusion" do |vb, override|
            # vb.vmx["memory"] = box[:memory]
            # vb.vmx["numvcpus"] = box[:cpu]
            vb.customize ["modifyvm", :id, "--cpus", box[:cpu]]
            vb.customize ["modifyvm", :id, "--memory", box[:memory]]
            override.vm.box = "centos7_fusion"
        end 
    end    
  end  
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
    config.vm.synced_folder "D:/meng/test1/abc", "/home/vagrant"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
    config.vm.provision "shell", inline: <<-SHELL
        # 删除docker
        sudo yum remove docker  docker-client  docker-client-latest  docker-common  docker-latest  docker-latest-logrotate  docker-logrotate  docker-engine

        # 安装docker
        sudo yum install -y yum-utils
        sudo yum-config-manager -y  --add-repo  https://download.docker.com/linux/centos/docker-ce.repo
        sudo yum install -y docker-ce

        # 添加权限
        sudo groupadd docker
        sudo usermod -aG docker vagrant
        # 启动docker
        sudo systemctl start docker
    SHELL
end
