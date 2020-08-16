Role Name
=========

This role is to install and execute a webserver in CentOS and Ubuntu.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

We create the file loadbalancer_vars.yml, because the file loadbalancer.j2 from directory templates, take the values of the vars to use in the virtualhost to act work a Proxy Reverse with balancer charge. 


Playbook
----------------

    - hosts: webserver
      remote_user: ansible
      become: yes
      become_method: sudo

      vars_files:
      - ./loadbalancer_vars.yml

      roles:
         -  role: apache-centos
            when: ansible_facts['os_family'] == "RedHat"
         -  role: apache-debian
            when: ansible_facts['os_family'] == "Debian"

License
-------

BSD

Author Information
------------------

Role created by Manuel Lanza and Etzequiel Urman
