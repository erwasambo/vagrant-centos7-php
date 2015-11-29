# Vagrant CentOS7 PHP Development Environment

This project sets up a CentOS 7.1 (64bit) virtual machine to run your PHP project in. It mounts your PHP project directory so that you can use your favorite editors to work.

## Requirements

* VirtualBox - Free virtualization software. [Download](https://www.virtualbox.org/wiki/Downloads)
* Vagrant - Tool for working with VirtualBox images. [Download](https://www.vagrantup.com/downloads.html)

## Tested on

|Host OS         |VirtualBox|Vagrant|
|----------------|---------:|------:|
|Mac OS X 10.10.5|5.0.10    |1.7.4  |
|Ubuntu 14.04    |4.3.28    |1.6.5  |

## What's in the Development Environment?

* PHP 7.0 (remi) (or 5.6, 5.5. See [group_vars/all](https://github.com/kenjis/vagrant-centos7-php/blob/master/provisioning/group_vars/all#L4-L5).)
  * Xdebug
  * Zend OPcache
  * APCu
* Apache 2.4.6
  * vhost setup for your PHP project
* MariaDB 5.5.44
* phpMyAdmin 4.4.15.1
* PHPUnit 5.0
* Composer 1.0-dev
* Git 1.8.3.1

## Directory Structure

~~~
project/                 ... your project directory
├── public/              ... web document root
└── vagrant-centos7-php/ ... this repository
~~~

If your web document root is not `public` folder, but the project folder, try to run the following commands:

~~~
$ cd /path/to/project/
$ ln -s . public
~~~

## How to Use

### Installation

~~~
$ cd /path/to/project/
$ git clone git@github.com:kenjis/vagrant-centos7-php.git
$ cd vagrant-centos7-php/
$ vagrant up
~~~

### Accessing Your Project

* Web
  * Port Forwarding: [http://localhost:8000/](http://localhost:8000/)
  * IP Address: [http://192.168.33.33/](http://192.168.33.33/)
  * phpMyAdmin: [http://localhost:8000/phpmyadmin/](http://localhost:8000/phpmyadmin/) (root password: `root`)

## Vagrant

Here are common commands:

|command|description|
|-------|-----------|
|`vagrant up`|starts the virtual machine and provisions it|
|`vagrant provision`|provisions the vagrant machine|
|`vagrant suspend`|will save the current running state of the machine and stop it|
|`vagrant halt`|attempts a graceful shutdown of the machine|
|`vagrant ssh`|gives you SSH access to the virtual machine|
|`vagrant destroy`|will destroy the machine|
|`vagrant status`|shows status of the machine|
|`vagrant global-status`|shows status of all virtual machines|

## References

* [Vagrant Documentation](https://docs.vagrantup.com/v2/)
* [Ansible Documentation](http://docs.ansible.com/ansible/index.html) (We use v1.9.4)
