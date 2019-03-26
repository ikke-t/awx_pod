awx_pod
=======

This Ansible role sets up Ansible AWX server using containers. It uses podman
to do it.

See this blog how to use it: https://redhatnordicssa.github.io/ansible-podman-containers-2

![awx-pod](https://redhatnordicssa.github.io/assets/images/awx-pod.png)

Requirements
------------

Role is tested on Fedora server.

Role Variables
--------------

Set AWX credentials and storage paths is ```defaults/main.yml``` file.

Dependencies
------------

Role depends on
[ikke_t.podman_container_systemd](https://galaxy.ansible.com/ikke_t/podman_container_systemd)
role. Also, at the time podman just got pieces together to run this, I needed
to use upstream version [podman-1.2.0-24.dev.git0458daf.fc31]() from [podman
koji downloads](https://koji.fedoraproject.org/koji/packageinfo?packageID=26289)


Example Playbook
----------------

```
- name: run AWX on host
  hosts: all
  tasks:
    - name: import awx_pod role to install it all
      vars:
        awx_admin_user: admin
        awx_admin_password: foobar
        awx_data_volume_host_path: /tmp/awx_data
        awx_db_volume_host_path: /tmp/awx_db
        awx_host_port: 8052/tcp
        #container_state: absent or running
      import_role:
        name: awx_pod
```

License
-------

GPLv3

Author Information
------------------

Ilkka Tengval
