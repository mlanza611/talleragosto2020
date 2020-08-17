Role Name
=========

This role is to install and execute a webserver in CentOS and Ubuntu.

Role Variables
--------------

We create the file loadbalancer_vars.yml, because the file loadbalancer.j2 from directory templates, take the values of the vars to use in the virtualhost to work as a Proxy Reverse with load balancer. 


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
