# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.

  config.vm.provider :virtualbox do |vb|
  # We need more power to operate smoothly
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--rtcuseutc", "on"]
    vb.customize ["setextradata", :id, "--VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]

  end

  config.vm.synced_folder "code/", "/var/www/html/", :nfs => true

  config.vm.box = "ubuntu/xenial64"
  config.ssh.insert_key = true
  config.ssh.forward_agent = true

  config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

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

  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.extra_vars = {
        MySqlRootPassword: 'rootpass',
        MySqlDatabaseName: 'drupal',
        MySqlDatabaseUser: 'drupal',
        MySqlDatabasePassword: 'geheim',
        ApacheWorkingDir: '/var/www/html',
        ApacheDocumentRoot: '/var/www/html/docroot',
        ApacheServerName: 'drupal.local'
      }
    end



end
