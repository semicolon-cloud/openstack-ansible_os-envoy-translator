========================
Team and repository tags
========================

.. image:: http://governance.openstack.org/badges/openstack-ansible-os_adjutant.svg
    :target: http://governance.openstack.org/reference/tags/index.html

.. Change things from this point on

OpenStack-Ansible Envoy-Translator
############################
:tags: openstack, envoy-translator, cloud, ansible
:category: \*nix

This Ansible role installs and configures Semicolon cloud envoy-translator.

This role will install the following Upstart services:
    * envoy-translator-api

Required Variables
==================

.. code-block:: yaml

    envoy-translator_service_password
    envoy-translator_rabbitmq_password
    envoy-translator_galera_password
    envoy-translator_galera_address

Example Playbook
================

.. code-block:: yaml

    - name: Install adjutant server
      hosts: envoy-translator_all
      user: root
      roles:
        - { role: "os_envoy-translator", tags: [ "os-envoy-translator" ] }
      vars:
        external_lb_vip_address: 172.16.24.1
        internal_lb_vip_address: 192.168.0.1
        envoy-translator_galera_address: "{{ internal_lb_vip_address }}"
        envoy-translator_galera_password: "SuperSecretePassword1"
        envoy-translator_service_password: "SuperSecretePassword2"
        envoy-translator_rabbitmq_password: "SuperSecretePassword3"
