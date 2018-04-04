cans.pip-config
===============

[![Build Status](https://travis-ci.org/cans/pip-config.svg?branch=master)](https://travis-ci.org/cans/pip-config)

Ansible Role to setup pip to access private package indices and other
Python package sources


Requirements
------------

This role has the requirements of Ansible's
[template](http://docs.ansible.com/ansible/template_module.html) module.


Role Variables
--------------

This role variables are namespaced using the `pip_config_` prefix.

- `pip_config_dir`: the directory in which install pip's configuration
  file (default: `~/.pip/`);
- `pip_config_index_url`: the main PyPI index you want pip to look for
  packages in (default: not defined);
- `pip_config_extra_index_urls`: the list of extra PyPI indexes you want
  pip to look for packages in (default: `[]`);
- `pip_config_file`: the name to give to pip configuration file
  (default: `pip.conf`);
- `pip_config_find_links_urls`: the list of extra web resources pip
  should scan for links to Python packages (default: `[]`);
- `pip_config_timeout`: the duration in seconds pip will wait for any
  package index to respond before droping the connexion and try with
  the next (default: 10).

You most likely do not need to modify the value of the `pip_config_dir`
and `pip_config_file` variables. But since pip supports many locations
for its configuration, these allow you to do it if you fancy it.

The `pip_config_timeout` variable you may want to adjust depending on
where are stored the packages you need. The lower the value, the less
you wait, but the higher the risk of unexpected failures.

If you want to add one or more PyPI indexes for pip to search in
addition to the default one, specify them as a list value for
`pip_config_extra_index_urls`.  If you want to override the default
PyPI index entirely, specify your own main index as a string value for
`pip_config_index_url`.  You can use both variables if you want pip
to ignore the default index *and* search multiple other PyPI indexes.

Dependencies
------------

This role has no dependencies.


Example Playbook
----------------

    - hosts: servers
      vars:
        pip_config_extra_index_urls:
          - https://my-pypi.domain.com/simple
        pip_config_find_links_urls:
          - https://my.domain.com/packages.html
           
      roles:
         - { role: "cans.pip-config" }


License
-------

The Ansible role pip-config is free software: you can redistribute it
and/or modify it under the terms of the GNU General Public License
version 2 as published by the Free Software Foundation.

pip-config is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with cans.package-sources. If not, see <http://www.gnu.org/licenses/>.


Author Information
------------------

Copyright © 2017, Nicolas CANIART
