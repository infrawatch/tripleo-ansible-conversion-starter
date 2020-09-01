Tripleo ansibilisation starter
==============================

This project container tooling to help you get started with using ansible to
deploy a stf client-side services in TripleO. To "ansibilise" a TripleO
service, you need to update the TripleO Heat template for the service, and also
to create a role that can be called from TripleO during deployment.

This tool:
  - creates a tripleo_<service> role, which is called by TripleO during
    the different deployment stages.
  - creates a <myservice>-container-ansible.yaml Heat template for use with
    THT, which consumes the tripleo_<service> role for deployment

To generate the role, use::

   ansible-playbook -i default.inv start_ansibilisation.yml

This creates the ``tripleo_<myservice>`` role in ``output_dir``, where
``myservice`` and ``output_dir`` default to ``test`` and ``~/output``,
respectively.

You can override these by modifying the ``default.inv`` file, or by passing
extra vars to ansible-playbook::

   ansible-playbook -i defauly.inv start_ansibilisation.yml -e myservice=someotherservice

Limitations
-----------

Currently, this tool only supports setting up a bare skeleton, as if for a new
service, and it is up to the user to port over functionality/logic from the
existing tripleo heat template.
Work is in progress on parsing existing THT templates and doing more of the
set-up work for porting to using ansible for deployment.

To try out this feature, pass the ``tht_input`` extra parameter to ansible::

   ansible-playbook -i default.inv start_ansibilisation.yml -e tht_input=/path/to/existing/template

If a ``tht_input`` is passed, the ``<myservice>-container-ansible.yaml`` is put
in the same directory as the existing template.

TODO
----
*
