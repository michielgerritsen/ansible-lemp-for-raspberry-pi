# Ansible Raspberry PI LAMP

This Ansible role will install the following on your Raspberry PI device(s):

- git
- composer
- mysql 5.5
- php-fpm 7.1
  * mcrypt
  * dom
  * curl
  * json
  * sqlite
- nginx
 
And adds your public key(s). You can run a Laravel installation on your Raspberry PI with this setup. This is tested on the model 2 and Zero W. Other versions should work also.

# Prerequisites

- Raspberry PI
- A fresh Raspbian installation
- SSH access

# How to run

*Change your hosts:*

Edit ``hosts``. Make sure to changed the IP-address and the hostname.

*Change the Github profile:*

Edit ``group_vars/all`` and change the used Github profile. Make sure you have added a public key to your Github account.
 
*Execute the command:*

``ansible-playbook site.yml``

*Warning: The first run*

If you did not yet added your SSH key, you should add ``--ask-pass`` to the command:

``ansible-playbook site.yml --ask-pass``

# Check if it all works

If all commands are completed, there is a ``phpinfo.php`` file created. You can check this by visiting ``http://your.host.ip.address/phpinfo.php``.

*mysql*
 
The ``pi`` user has an ``.my.cnf`` file which logs you in automatically by running ``mysql`` from the command line. The default user is ``mysql``, without an password. Creating a database is as simple as:
 
``mysql -e "create database if not exists DATABASENAME;"``
