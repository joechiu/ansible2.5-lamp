Building a simple LAMP stack and deploying Application using Ansible Playbooks.
-------------------------------------------

This exmple is an enhancement from an existing git module. Please refer to 
the git for the original codes: 
https://github.com/ansible/ansible-examples/tree/master/lamp_simple_rhel7

The changes in this example are about to complete the proper migration from 
local site to remote servers including rollback, lamp installations and 
archive/unarchive the zipped files for httpd service and mysql database. The 
changes also enable the automation infrastructure for the mysql installation.

These playbooks require Ansible 2.x and Centos 7.5 in the remote servers.

These playbooks are meant to be a reference and starter's guide to building
Ansible Playbooks. These playbooks were tested on CentOS 7.5 so I recommend
that you use CentOS or RHEL to test these modules.

RHEL7.5 version reflects changes in Red Hat Enterprise Linux and CentOS 7.5:
1. Network device naming scheme has changed
2. iptables is replaced with firewalld
3. MySQL is replaced with MariaDB

This LAMP stack can be on a single node or multiple nodes. The inventory file
'hosts' defines the nodes in which the stacks should be configured.

        [webservers]
        localhost

        [db]
        dbserver

Here the webserver would be configured on the local host and the dbserver on a
server called "dbserver". The stack can be deployed using the following
command:

        ansible-playbook -i hosts site.yml

Once done, you can check the results by browsing to http://localhost/index.php.
You should see a simple test page and a list of databases retrieved from the
database server.
