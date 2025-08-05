[![CI](https://github.com/de-it-krachten/ansible-role-chocolatey/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-chocolatey/actions?query=workflow%3ACI)


# ansible-role-chocolatey

Install chocolay on Windows hosts and managed chocolatey packages



## Dependencies

#### Roles
None

#### Collections
- chocolatey.chocolatey
- chocolatey.chocolatey

## Platforms

Supported platforms

- Windows Server 2012 R2<sup>1</sup>
- Windows Server 2016<sup>1</sup>
- Windows Server 2019<sup>1</sup>
- Windows Server 2022<sup>1</sup>
- Windows Server 2025<sup>1</sup>

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Chocolatey installation script
chocolatey_bootstrap_script: https://community.chocolatey.org/install.ps1

# Chocolatey repository
chocolatey_repository: https://community.chocolatey.org/api/v2/

# Should the default public source be delete
chocolatey_delete_public_source: false

# Extra sources to configure
chocolatey_sources: []

# List of chcolatey packages to install
chocolatey_packages: []

# Update package to latest version
chocolatey_package_update: false

# Proxy for connecting to repository & software packages
# chocolatey_proxy_url: http://127.0.0.1:3128
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'chocolatey'
  hosts: all
  become: 'yes'
  vars:
    chocolatey_packages:
      - putty.install
      - name: mobaxterm
        ignore_checksums: true
  tasks:
    - name: Include role 'chocolatey'
      ansible.builtin.include_role:
        name: chocolatey
</pre></code>
