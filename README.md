devbox
======

A vagrant development vm provisioned for working with PHP and the Laravel framework out of the box. 


## Features / Stack
Ubuntu 12.04 32bit, Nginx, PHP5.4, php-fpm, MySQL 5.5, Redis, Beanstalkd, supervisord, Sphinx, localtunnel, Node.js, MongoDB



## Requirements

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) - Free virtualization software 
* [Vagrant](https://www.vagrantup.com) - Tool for working with VirtualBox images


## Initial Setup

* Clone this repository `git clone https://github.com/Aboalarm/devbox.git`. 
* Run `vagrant up` inside the newly created directory. (the first time you run Vagrant it will fetch the virtual box image which is ~300mb. So this could take some time)
* Vagrant will now use Puppet to provision the devbox (this could take a few minutes)
* Point "devbox" and any other vhosts to `192.168.3.3` in your hosts file of your OS. e.g. `192.168.3.3 devbox myproject.dev myotherproject.dev` 
* Now just clone/copy your Laravel projects into `www/[HOSTNAME]` and open http://[HOSTNAME] in your browser. **Done!** 

## Shared Folders
The www folder is automatically synced to the VM (/var/www). This is why we clone our Laravel project into this folder. The sync works in both directions. So any files generated by Laravel (/storage folder for example) will be accessible from your host machine. 

## Credentials 
* SSH User: `vagrant` PW: `vagrant`
* MySQL User: `root` PW: `root` (access MySQL through SSH)

## Vagrant Commands

* `vagrant up` starts the virtual machine and provisions it
* `vagrant ssh` gives you shell access to the virtual machine
* `vagrant suspend` will essentially put the machine to 'sleep' with `vagrant resume` waking it back up
* `vagrant reload` will reload the VM. Do this when the VM config changed. For exmpale when you changed one of the configs (e.g. php.ini, sphinx.conf, etc. or after a git pull of this repo)
* `vagrant halt` attempts a graceful shutdown of the machine and will need to be brought back with `vagrant up`
* `vagrant halt --force` force shutdown if normal halt doesn't work
* `vagrant destroy` you broke something? this will destroy the VM and reprovisions it again completely. Takes some time.



Fore more: Vagrant is [very well documented](http://docs.vagrantup.com/v2/)
