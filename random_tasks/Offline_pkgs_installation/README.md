## Support ticket || 15-Jun-23


We received a support request to install "NFS-Client" and mount a directory with NFS server on IB production VMs.

The required information are below.

- NFS server IP: 192.168.190.30
- Targeted VM list:

    - 192.168.190.70
    - 192.168.190.71
    - 192.168.190.73

- Mount path on client side: /var/lib/celloscope/csb/csb-platform/data/localfileserver
- Shared directory on sever side: /var/lib/celloscope



## Procedure 

IB is isolated from untrusted network. So, we will install the packages by using offline installation.

So, first we download the required packages and dependencies by using below cmd on a workstation who can able to reach internet.
```
apt install --download-only <package name> -y
```
The deb files are downloaded on "/var/cache/apt" directory. We moved the files to "ib_prod_15-Jun-23" directory.


## Ansible playbooks

List the targeted VMs IP

    inventory

Downloaded packages are sent  from local machine to ib VMs.

    copy_pkgs_playbook.yaml

Install NFS client packages

    install_pkgs_playbook.yaml

Core configuration changes for NFS client VMs

    nfs_client_config_playbook.yaml

Enable and restart the service

    services_playbook.yaml

Entry for variables

    vars

Final playbook

    final_playbook.yaml


## Install by Ansible
```
ansible-playbook final_playbook.yaml
```


## Check after installation

Check the service status
```
ansible prod -m shell -a "systemctl status nfs-common.service | grep Active"
```

Check the mount point
```
ansible prod -m shell -a "df -hT | grep nfs4"
```