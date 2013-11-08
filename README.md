Ansible Configuration For Deploying CiviCRM
===========================================

This configuration will deploy a fresh CiviCRM (Wordpress) install to a remote host.

This configuration was created for use at [Grand Rapids Give Camp 2013](http://grgivecamp.org/)

The targeted host is Digital Ocean - but would work just as well on any host running Ubuntu 12.04 and up with ssh support.

Installation
------------
Requires [Ansible](http://www.ansibleworks.com/docs/intro_installation.html)

Usage
----- 
Deploying is easy. Configure the hosts file with your user/host combos.

```
[user]
123.456.78.90
234.567.89.10
```

With your hosts file configured you can run the `ansible-playbook` command from the root of this repository like so:

```
ansible-playbook civicrm.yml -i hosts 
```

This will provision a LAMP stack on the remote host, install the latest wordpress, and grab the specified version of CiviCRM.

The file `group_vars/all` contains configuration values for specifying mysql version, CiviCRM version, and database credentials.

Digital Ocean
-------------
*Note for digital ocean:* Digital ocean was a little wonky with SSH keys, this [article](https://www.digitalocean.com/community/articles/how-to-set-up-ssh-keys--2) was helpful. Basically after adding your key to digital ocean, you should run something like this on your local machine before running the playbook:

cat ~/.ssh/id_rsa.pub | ssh root@123.45.56.78 "cat >> ~/.ssh/authorized_keys"