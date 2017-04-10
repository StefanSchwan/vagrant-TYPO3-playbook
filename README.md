# Vagrant TYPO3 Playbook

An Ansible Playbook to setup a Vagrant Box running TYPO3

## Requirements

Requires [Vagrant](https://www.vagrantup.com/), [Virtualbox](https://www.virtualbox.org/) and [Ansible](https://www.ansible.com/)

## Starting the VM

Edit your Hostfile to include

```
192.168.33.10 typo3.local
```
Use your terminal to cd into the cloned dir and run
```
vagrant up
```


to start the Provisioner. By default, the TYPO3 Backend will be available on http://typo3.local/typo3.

## Vagrantfile
The Vagrantfile holds all Configuration for the Machine, the admin user name and password can also be set there. Be aware that changing the values after the first ansible run will properly break things, so if you want to change anything do it before issuing ```vagrant up``` the first time.

## Filesharing
the code/ Folder gets mounted into the machine as the Apache Working Directory, code/docroot will be the Documentroot.

## Composer and typo3-console
The Composer File in code/composer.json is setup to install TYPO3 8.7, [TYPO3-Console/typo3_console](https://github.com/TYPO3-Console/typo3_console) and [helhum/dotenv-connector](https://github.com/helhum/dotenv-connector).
The installation is performed by Ansible via TYPO3-Console/typo3_console.
