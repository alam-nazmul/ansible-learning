## You can specify ranges in the host names or IP addresses to simplify Ansible host inventories. You can specify either numeric or alphabetic ranges. Ranges have the following syntax

[START:END]

## Samples

`192.168.[4:7].[0:255]`

`server[01:20]`

`[a:c].dns.example.com`

`2001:db8::[a:f]`


## Examples_1

[usa]

washington[1:2].example.com


[canada]

ontario[01:02].example.com

