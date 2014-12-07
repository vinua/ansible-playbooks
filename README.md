Ansible Playbooks
=================

[Ansible Documentation][1]

[1]: http://docs.ansible.com/index.html


Usage
-----

    $ git clone https://github.com/vinua/ansible-playbooks.git
    $ cd ansible-playbooks

Rename and edit `hosts_example` to `hosts` then run:

    $ export DO_CLIENT_ID=XXX DO_API_KEY=XXX
    $ python2 digital_ocean_vars.py > digital_ocean_vars.yml
    $ ansible-playbook -i hosts bootstrap.yml

Wait for DNS propagation then run:

    $ ansible-playbook -i hosts provision.yml
