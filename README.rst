Tripleo ansibilisation starter
==============================

This project container tooling to help you get started with using ansible to
deploy a stf client-side services in TripleO. To "ansibilise" a TripleO
service, you need to update the TripleO Heat template for the service, and also
to create a role that can be called from TripleO during deployment.

This tool creates a tripleo_<service> role, which is called by TripleO during
the different deployment stages.

To generate the role, use::

   ansible-playbook -i default.inv start_ansibilisation.yml

This creates the ``tripleo_<myservice>`` role in ``output_dir``, where
``myservice`` and ``output_dir`` default to ``test`` and ``~/output``,
respectively.

You can override these by modifying the ``default.inv`` file, or by passing
extra vars to ansible-playbook::

   ansible-playbook -i defauly.inv start_ansibilisation.yml -e myservice=someotherservice
