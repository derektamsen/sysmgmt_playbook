Building a simple LAMP stack and deploying Application using Ansible Playbooks.
-------------------------------------------

These playbooks require Ansible 2.9.

These playbooks are meant to be a reference and starter's guide to building
Ansible Playbooks. These playbooks were tested on CentOS 6.x so we recommend
that you use CentOS or RHEL to test these modules.

This LAMP stack can be on a single node or multiple nodes. The inventory file
'production' defines the nodes in which the stacks should be configured.

        [webservers]
        localhost

        [dbservers]
        bensible

Here the webserver would be configured on the local host and the dbserver on a
server called "bensible". The stack can be deployed using the following
command:

        ansible-playbook -i production site.yml

Once done, you can check the results by browsing to http://localhost/index.php.
You should see a simple test page and a list of databases retrieved from the
database server.

Development and Deploy Setup
----------------------------

        pip3 install --upgrade virtualenv
        python3 -m venv venv
        . venv/bin/activate
        pip install -r requirements.txt

Usage
-----

Install Ansible

        sudo apt-get install software-properties-common
        sudo apt-add-repository ppa:ansible/ansible
        sudo apt-get update
        sudo apt-get install ansible git

Run ansible locally

        ansible-pull -U https://github.com/derektamsen/sysmgmt_playbook.git \
          --inventory production \
          site.yml

Run ansible for specific roles against remote hosts

        ansible-playbook site.yml -i production --limit retropies

List facts from host

        ansible -i production -m setup hostname

Create a new role playbook

        ansible-galaxy init roles/new-playbook-name

View ansible encrypted files

        ansible-vault view group_vars/<role>/<file>

View ansible encrypted variables

        ansible localhost -m ansible.builtin.debug -a var="<var_to_view>" -e "@path/to/file.yml"

Encrypt ansible variable

        ansible-vault encrypt_string
