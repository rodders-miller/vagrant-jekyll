# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # setup of the memory for the libvirt provider to assign 1GB of memory 
  config.vm.provider "libvirt" do |jekyllbox|
      jekyllbox.memory = 1048
  end
  
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 4000, host: 8080

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
  # config.vm.synced_folder "../data", "/vagrant_data"
  config.vm.synced_folder ".", "/vagrant", type: "rsync"

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
  # information on availecho I am provisioning...able options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.


#config.vm.provision "file", source: "jboss-fuse-full-6.2.1.redhat-084.zip", destination: "jboss-fuse-full-6.2.1.redhat-084.zip"

$script = <<SCRIPT

echo I am provisioning...
apt-get update -y
apt-get -y install make gcc

# 1.) First install Ruby as per https://www.brightbox.com/docs/ruby/ubuntu/

apt-get -y install software-properties-common
apt-add-repository -y ppa:brightbox/ruby-ng
apt-get update -y
sudo apt-get -y install ruby2.2 ruby2.2-dev

# 2.) Next install Jekyll
gem install jekyll bundler



SCRIPT

config.vm.provision "bootstrap", type: "shell" do |s|
 s.inline = $script
end

#apt-get -y install ruby ruby-dev make gcc
#gem install jekyll bundler

# apt-get ruby installs a older version of Ruby not compatable with Jekyll v3 - needs to be version 2 or higher
#Use ruby-intsall to get the latest stable version of Ruby (e.g. 2.4) 
# see https://github.com/postmodern/ruby-install#readme
#wget -O ruby-install-0.6.1.tar.gz https://github.com/postmodern/ruby-install/archive/v0.6.1.tar.gz
#tar -xzvf ruby-install-0.6.1.tar.gz
#cd ruby-install-0.6.1/
#make install
#ruby-install



end
