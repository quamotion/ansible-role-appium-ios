appium-ios Role
===============

This Ansible role deploys Appium to a machine running Debian or Ubuntu Linux,
and adds support for running Appium tests on iOS devices.

This Ansible role will configure Appium to run as a SystemD service.

Requirements
------------

This role installs Appium and software from [Quamotion](http://docs.quamotion.mobi),
which enables iOS support. You'll need a seperate license from Quamotion for
xcuitrunner if you want to run tests on iOS devices.

Role Variables
--------------

| Variable                 | Default    | Description
|--------------------------|------------|-------------------------------------------
| `appium_version`         | `1.15.1`   | The version of Appium to install
| `quamotion_version`      | `0.150.70` | The version of the Quamotion utility (xcuitrunner) to install
| `license_file_path`      |            | If available, the path to your Quamotion license file
| `developer_profile_path` |            | If available, the path to your iOS Developer Profile
| `devimg_dir`             |            | If available, the path to the directory which contains your Developer Disk images
| `appium_user`            | `appium`   | The name of the service account for the Appium service

Dependencies
------------

- This role uses the [geerlingguy.nodejs](https://github.com/geerlingguy/ansible-role-nodejs) role to deploy node.js

Example Playbook
----------------

The following playbook file will deploy the `appium-ios` role to a host named `rpi`:

```yaml
---
- hosts: rpi
  become: true
  vars:
    license_file_path: /etc/quamotion/.license
    developer_profile_path: etc/quamotion/quamotion.developerprofile
    devimg_dir: /etc/quamotion/devimg/
  roles:
  - appium-ios
```

License
-------

MIT

Author Information
------------------

This role is authored by [Quamotion](http://docs.quamotion.mobi).

Quamotion provides commercial software which allows you to automate
iOS devices using Linux or Windows.