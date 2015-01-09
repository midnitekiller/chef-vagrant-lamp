# Intoduction

This cookbook deploys a LAMP stack with Ioncube loader for zend framework to deploy the aMember application.

# Getting Started

This cookbook works with precise64 with chef version 11 and up.

To get started simply clone the repo and run the following commands to configure the project

```
$ bundle install
$ berks install
```

# Requirements 

1. [Vagrant] (http://www.vagrantup.com) 1.4.3
2. [Virtualbox] (https://www.virtualbox.org) 4.3.6 
3. [Chef-client] (http://www.getchef.com/chef/install/) 11.8.2 _(Windows)_
4. [Git] (http://git-scm.com) 1.8.5.2 
5. [Ruby] (http://rubyinstaller.org) Installer 1.9.3 p484 _(Windows)_
6. [Devkit] (http://rubyinstaller.org/add-ons/devkit/) tdm 32-4.5.2 _(Windows)_

# Usage

## Vagrant

### Provisioning

To provision the vagrant box run the following command.

`$ vagrant up --provision`

This will create a new virtualbox and pre configure the development environment

If you receive and error that the box is missing you can install the vagrant box by running

`$ vagrant box add precise64 http://files.vagrantup.com/precise36.box`

a list of available boxes will be found [here] (http://www.vagrantbox.es)

### Login

To login to the vagrant box

`$ vagrant ssh`

### Initial Configration
`$ a2ensite` to enable apache default site

`$ cp /usr/local/src/loader-wizard.php /var/www` to copy sources to web root

you can now browse [http://33/33/33/122/loader-wizard.php](http://33/33/33/122/loader-wizard.php) for setup

## Cloud Provisioning

To provision the environment on a virtual server, knife solo is used, run the following command to do an initial chef configuration and a chef run.

`$ knife-solo bootstrap username@host -i ~/.ssh/yoursshkey -N test`

Then follow the same configuration steps on your server from above.

## Deploying changes

To deploy changes run the following

`$ knife-solo cook username@host -i ~/.ssh/yoursshkey -N test`

# Contributions

Just fork the cookbook and feel free to enhance.

# Author

Lief Jill Colegado
		
DevOps Appfibre

liefjillcolegado@gmail.com
