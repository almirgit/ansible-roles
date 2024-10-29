# Example of use export-nfs-directory ansible role

Directory structure needed:
```
$ tree -a
.
├── ansible.cfg
├── inventory
├── roles
│   ├── ansible-roles--setup-nfs-client -> /home/almir/git/ansible/ansible-roles/ansible-roles--setup-nfs-client/
│   └── ansible-roles--setup-nfs-server -> /home/almir/git/ansible/ansible-roles/ansible-roles--setup-nfs-server/
├── test-role-setup-nfs-client.yml
└── test-role-setup-nfs-server.yml
```

```yaml
---
  - name: Test export-nfs-directory
    hosts: nur2.example.com
    become: true

    roles:
      - role: setup-nfs-server
        rvar_os_type: "rhel_8"
        rvar_export_directory: "/exports/wpbackup"
        rvar_client_server: "nur4.example.com"
        rvar_mnt_dir_owner: root
        rvar_mnt_dir_group: root
```