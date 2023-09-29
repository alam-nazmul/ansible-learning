## Support ticket || 15-Jun-23


We received a support request to install "NFS-Client" and mount a directory with NFS server on IB production VMs.

The required information are below.

- NFS server IP: 192.168.190.30
- Targeted VM list (Node-1 192.168.190.205):

    - 192.168.190.16
    - 192.168.190.21
    - 192.168.190.60
    - 192.168.190.53
    - 192.168.190.37
    - 192.168.190.38
    - 192.168.190.39
    - 192.168.190.18
    - 192.168.190.62
    - 192.168.190.70
    - 192.168.190.73
    - 192.168.190.80
    - 192.168.190.213
    - 192.168.190.214
    - 192.168.190.231
    - 192.168.190.232

- Targeted VM list (Node-2 192.168.190.206):
    - 192.168.190.10
    - 192.168.190.11
    - 192.168.190.12
    - 192.168.190.13
    - 192.168.190.14
    - 192.168.190.15
    - #192.168.190.17 // Can't access this VM directly from my PC. So, I changed the clock manually.
    - 192.168.190.20
    - 192.168.190.23
    - 192.168.190.24
    - 192.168.190.25
    - 192.168.190.27
    - 192.168.190.28
    - 192.168.190.29
    - 192.168.190.30
    - 192.168.190.31
    - 192.168.190.33
    - 192.168.190.34
    - #192.168.190.35 // Can't access this VM directly from my PC. So, I changed the clock manually.
    - 192.168.190.36
    - 192.168.190.41
    - 192.168.190.42
    - 192.168.190.43
    - 192.168.190.44
    - 192.168.190.45
    - 192.168.190.46
    - 192.168.190.47
    - 192.168.190.48
    - 192.168.190.52
    - 192.168.190.71
    - 192.168.190.72
    - 192.168.190.216
    - 192.168.190.217
    - 192.168.190.218
    - 192.168.190.233

- Set timezone to Asia/Dhaka
- Set the clock manually



## Procedure 

First need to previlige "ubuntu" user as sudo user.
```
visodu
    ubuntu  ALL=(ALL) NOPASSWD: ALL
```


## Ansible playbooks

List the targeted VMs IP

    inventory

Ansible playbook for update the clock

    sync_with_localtime_playbook.yaml


## Update clock by Ansible
```
ansible-playbook sync_with_localtime_playbook.yaml
```

## Update clock by Manually
```
timedatectl set-timezone "Asia/Dhaka"
timedatectl set-time '2023-06-16 02:10:10'
```

## Check after installation

Check the service status
```
ansible prod -m shell -a "timedatectl | grep Local"
```
