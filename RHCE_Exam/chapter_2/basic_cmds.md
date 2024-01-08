## Verifying the Inventory

`ansible washington1.example.com --list-hosts`

`ansible washington01.example.com --list-hosts`

`ansible canada --list-hosts`

## Checked the hosts list

`ansible all --list-hosts`

`ansible webservers --list-hosts`

## Checked the hosts list from inverntory file

`ansible all -i inventory --list-hosts`


## Checked the hosts list from which is not in inverntory file

`ansible ungrouped -i inventory --list-hosts`


## Checked the hosts list from inverntory file which are belongs in a group

`ansible production -i inventory --list-hosts`

## One of the simplest ad hoc commands uses the ping module. This module does not do an ICMP ping, but checks to see if you can run Python-based modules on managed hosts.

`ansible all -m ping`

## Find the ansible modules and see in details

`ansible-doc -l | grep copy`

`ansible-doc copy`


## Ansible modules

![MOdules](<Screenshot from 2024-01-09 02-50-20.png>)