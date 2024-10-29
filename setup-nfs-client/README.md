# Example of use export-nfs-directory ansible role

Directory structure needed:
```
$ tree -a
.
├── ansible.cfg
├── inventory
├── roles
│   ├── setup-nfs-client -> /home/almir/git/ansible/ansible-roles/setup-nfs-client/
├── test-role-setup-nfs-client.yml
└── test-role-setup-nfs-server.yml
```

```yaml
---
  - name: Test export-nfs-client
    hosts: nur2.example.com
    become: true

    roles:
      - role: setup-nfs-client
        rvar_os_type: "debian_11"
        rvar_nfs_server: "nur2.koderacloud.net"
        rvar_export_directory: "/exports/wpbackup"
        rvar_mount_directory: "/mnt/nfs/db1/wpbackup"
```