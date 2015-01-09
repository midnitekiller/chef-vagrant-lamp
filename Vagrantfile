# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 1.5.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  config.vm.hostname = "chef-lamp-berkshelf"

  # Set the version of chef to install using the vagrant-omnibus plugin


  config.omnibus.chef_version = :latest
  config.berkshelf.enabled = true
  config.cache.auto_detect = true
  config.cache.scope = :machine

  config.vm.box = "ubuntu-14.04"


  config.vm.network :public_network, ip: "192.168.1.33"
  config.vm.network :private_network, ip: "33.33.33.33"

  # config.vm.provider :virtualbox do |vb|
  #   vb.customize ["modifyvm", :id, "--memory", "1024"]
  # end

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = %w(cookbooks berks-cookbooks site-cookbooks)
    chef.roles_path     = 'roles'
    chef.data_bags_path = 'data_bags'
    chef.json = {
      mysql: {
        server_root_password: 'rootpass',
        server_debian_password: 'debpass',
        server_repl_password: 'replpass'
      }
    }

    chef.add_recipe "apt"
    chef.add_recipe "build-essential"
    chef.add_recipe "git"
    chef.add_recipe "vim"
    chef.add_recipe "php"
    chef.add_recipe "php::module_mysql"
    chef.add_recipe "apache2"
    chef.add_recipe "apache2::mod_php5"
    chef.add_recipe "apache2::mod_rewrite"
    chef.add_recipe "mysql::server" 
    chef.log_level = :debug
  end

end
