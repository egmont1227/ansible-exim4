Exim setup
========
[![Build Status](https://travis-ci.org/Blue-Bag/ansible-exim4.svg?branch=master)](https://travis-ci.org/Blue-Bag/ansible-exim4)

Ansible role to install and configure Exim4 on Debian based system.

Role Variables
--------------

The following variables are used for the content of the /etc/exim4/update-exim4.conf.conf file

* *exim4_dc_eximconfig_configtype*
* *exim4_dc_other_hostnames*
* *exim4_dc_local_interfaces*
* *exim4_dc_readhost*
* *exim4_dc_relay_domains*
* *exim4_dc_minimaldns*
* *exim4_dc_relay_nets*
* *exim4_dc_smarthost*
* *exim4_CFILEMODE*
* *exim4_dc_use_split_config*
* *exim4_dc_hide_mailname*
* *exim4_dc_mailname_in_oh*
* *exim4_dc_localdelivery*
* *exim4_catch_all_email*
* *exim4_passwd_client*: Account and password data for SMTP authentication when exim is authenticating as a client to
   some remote server as a list.

Usage
-----

```
  roles:
    - role: exim4
      exim4_dc_eximconfig_configtype: 'satellite'
      exim4_dc_use_split_config: 'false'
      exim4_dc_readhost: 'lacaisse.com'
      exim4_dc_smarthost: 'smtp.mandrillapp.com::587'
      exim4_dc_hide_mailname: 'true'
      exim4_catch_all_email: 'somemail@example.com'
      exim4_passwd_client: ['*.mandrillapp.com:your-mandrill-username@yourdomain.com:{{ mandrill_api_key }}']
```
Testing:

   echo "test mail from new server." | mail -s "Test message" somone@somewhere.tld

   Could also test the configuration file prior to restart:
   exim -bV

License
-------

BSD

Author Information
------------------
Fork: George Boobyer

* Pierre Buyle <buyle@floedesign.ca>
* Pierre Paul Lefebvre <lefebvre@studioqi.ca>

Forked from https://github.com/Pheromone/ansible-exim4 - now https://github.com/FloeDesignTechnologies/ansible-exim4

