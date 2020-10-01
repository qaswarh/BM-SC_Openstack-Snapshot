# BM-SC_Openstack-Snapshot
This playbook provide nova list on instances filtered as per grep on [BM-SC](https://www.etsi.org/deliver/etsi_ts/123200_123299/123246/14.01.00_60/ts_123246v140100p.pdf) string common amongst all VMs of VNF. It's one time job to figure what is commont string which amongst all instances of BM-SC VNF. Replace the 'BM-SC string' with actual common string for nova list to come up with only desired VMs. The playbook then pause and ask the user to choose the instance to take the snapshot. 

The playbook advise to take the snapshot of standby/slave nodes first. Another repository 'BM-SC_VNF-Status' has a playbook to figure-out Master DB and Active CP/UP nodes

The playbook check the VM status prior to shutdown and creating the snapshot, once user has chosen the instance. The playbook introduces appropriate pause time to get the task completed before jumping to the next task. The instance is brought back to service after snapshot creation, the last task in this playbook.

The playbook [Set environment variables using the OpenStack RC file](https://docs.openstack.org/ocata/user-guide/common/cli-set-environment-variables-using-openstack-rc.html) each time nova command is issued.

Hostname where Ansible control node will connect using ansible_connection=ssh, ansible_user=user and ansible_ssh_pass=password information should be in the inventory/hosts. I introduced ansible_ssh_private_key_file=.ssh/id_rsa in my ~ as I'm authorized in .ssh/authorized_keys in my home dir which is also my home dir of Ansible control node
