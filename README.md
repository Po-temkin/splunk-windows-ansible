# splunk-enterprise
This repository contains set of playbooks which could be used to deploy Distributed Splunk Enterprise environment on Windows Server via WinRM.
I used this playbooks to deploy Splunk in my company.

## Table of content
1. Description
1. Getting Started
1. List of playbooks

#### Desctiption
In each playbook you can find some usable information in header-comment.
Header contains the following sections:
* Tested on:
    * Version of environment in which playbook tested
* Description:
    * Desctiption of playbook
* Input: 
    * List of required variables and some information about each of it
* Output: 
    * List of output variables if they exist
* Requirements
    * Required additional information 

#### Getting Started
#### Getting started with this playbooks will requires you to:
1. Ansible controller
1. Couple of VMs with Windows Server onboard
1. Splunk Enterprise installer
1. Powershell module Psini in ZIP archive
1. LDAP and SMTP server (if you need it)
1. Correct inventory file
1. 'Master' playbook (spl_deploy.yml) with defined variables and all needed tasks

#### Ansible
In our company we using Ansible 2.9 for some reasons. I can't test this set on Ansible > 2.9 so be carefully when yoi run it on different Ansible version.

#### VMs
I could be wrong but the minimum amount of servers according to documentation are:
* 1 server for manager node role
* 1 server for search head deployer role
* 3 servers for indexer cluster
* 3 servers for serch head cluser
* If you have small production environment you can run first roles on one VM

#### Splunk Installer
Download Splunk Installer (*.exe) and put it in place that ansible controller have access to.

#### Psini module
Powershell Psini module is used to manage Splunk ini configuration files.
Because servers in our company haven't access to PS Galery i am download module on PC with desired access and then archive it.
Put Psini *.zip file in place that ansible controller have access to if you have the same situation or use another ways to install it.

#### LDAP and SMTP server
You need this servers if you want to authenticate in Splunk via LDAP and send notification.

#### Inventory
Determine varibles which represented in example host.ini file.
Aslo determine role of each VM using the following groups:
* spl_idx - Members of indexer cluster
* spl_mn - Manager node server
* spl_sh - Members of search head cluster
* spl_shd - Search head deployer server

#### Master Playbook
To run all set of playbooks you need to set up spl_deploy correctly. In this file you determine most of variables and select which playbooks you need to run. Example spl_deploy.yml file contain all playbooks but you can delete some if you understand that you don't need it.

#### List of playbooks
