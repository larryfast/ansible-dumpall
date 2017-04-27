Dumpall
========

Dump all ansible variables into a file on localhost
Based on the excellent work by [Lester Wade](https://coderwall.com/p/13lh6w)!

NOTE: extra-vars, role-vars and a few other hidden variable sets are not yet included.

Requirements
------------

None.

Role Variables
--------------

    dumpall_localhost_destination: ./dump_vars.json

Example Playbook
-------------------------

The following code can be run stand alone to demo the role.
Or append it at the end of any playbook.

    - hosts: localhost
      connection: local
      tasks:
        # All Registered Tasks will appear in the dump
        - name:     hello_server_cmd
          register: hello_server_cmd
          shell:    "echo Hello World from `hostname` User `whoami` PWD `pwd`"
          changed_when:  False

    - hosts: localhost
      gather_facts: yes
      connection: local
      roles:
         - { role: ansible-dumpall, dumpall_localhost_destination: ./dump_vars.json }

License
-------

LGPL

Author Information
------------------

Jasper N. Brouwer, jasper@nerdsweide.nl

Ramon de la Fuente, ramon@delafuente.nl

Larry Fast, lfast1960 at yahoo dot com
