# BM-SC_Openstack-Snapshot
This playbook provide nova list on instances filtered as per grep on [BM-SC](https://www.etsi.org/deliver/etsi_ts/123200_123299/123246/14.01.00_60/ts_123246v140100p.pdf) string common amongst all VMs of VNF. The playbook then pause and ask the user to choose the instance to take the snapshot. 

Note: It's one time job to figure what is commont string which amongst all instances of BM-SC VNF. Replace the 'BM-SC string' with actual common string for nova list to come up with only desired VMs.

The playbook advises to take the snapshot of standby/slave nodes first. [BM-SC_VNF_Status](https://github.com/qaswarh/BM-SC_VNF_Status) has a playbook to figure-out Master DB and Active CP/UP nodes

The playbook check the VM status prior to shutdown and creating the snapshot, once user has chosen the instance. The playbook introduces appropriate pause time to get the task completed before jumping to the next task. The instance is brought back to service after snapshot creation, the last task in this playbook.

The playbook [Set environment variables using the OpenStack RC file](https://docs.openstack.org/ocata/user-guide/common/cli-set-environment-variables-using-openstack-rc.html) each time nova command is issued. Make sure RC file is exporting username and password for Openstack without asking or prompting to user for input. # - out  any such echo or read line.

Hostname, ansible_connection=ssh, ansible_user=user and ansible_ssh_pass=password should be in the inventory/hosts file for playbook to use. I didn't use ansible_ssh_pass=password but introduced ansible_ssh_private_key_file=.ssh/id_rsa instead as I was authorized under .ssh/authorized_keys in home dir. 
And this dir was also my home for Ansible control node
