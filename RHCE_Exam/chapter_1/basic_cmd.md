## Install Ansible on RHEL

`yum list installed platform-python`

`yum module install python36 -y`

`yum install ansible -y`


## Verify that Ansible is installed on the system.

`ansible --version`


## Verify the ansible_python_version on the localhost by using the setup module

`ansible -m setup localhost | grep
ansible_python_version`
