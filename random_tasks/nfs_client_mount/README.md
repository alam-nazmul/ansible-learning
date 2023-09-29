## Support ticket || 21-Jun-23

We received a support request to modify NFS-Client mount directory  with NFS server on IB production VMs.

The required information are below.

- NFS server IP: 192.168.190.30
- Targeted VM list:

    - 192.168.190.70
    - 192.168.190.71
    - 192.168.190.73

- Current mount path on client side: /var/lib/celloscope/csb/csb-platform/data/localfileserver
- Proposed mount path on client side: /var/lib/celloscope
- Shared directory on sever side: /var/lib/celloscope


## Checklist

- Unmount the current NFS mount point
- Remove the current mounted directory
- Create a new NFS directory as per requirement. 
- Mount the NFS with new directory
- Remove the old mount point from "/etc/fstab"


## Ansible playbooks

List the targeted VMs IP

    inventory

Modify the core configuration changes for NFS client VMs

    nfs_client_config_playbook.yaml

Enable and restart the service

    services_playbook.yaml

Final playbook

    final_playbook.yaml


## Install by Ansible
```
ansible-playbook final_playbook.yaml
```


## Check after installation

Check the filesystem file's entry
```
ansible prod -m shell -a "cat /etc/fstab | grep nfs"
```

Check the mount point
```
ansible prod -m shell -a "df -hT | grep nfs4"
```