# BM-SC_Openstack-Snapshot
This playbook provide nova list on instances filtered as per grep on BM-SC string common amongst all VMs of VNF. The playbook then pause and ask the user to choose the instance to take the snapshot. 

The playbook advise to take the snapshot of standby/slave nodes first. Another repository 'BM-SC_VNF-Status' has a playbook to figure-out Master DB and Active CP/UP nodes

The playbook check the VM status prior to shutdown and creating the snapshot, once user has chosen the instance. The playbook introduce appropriated pause to get the task completed before jumping to next task. The instance is brought back to service after snapshot creation, the last task of this playbook.

The playbook [Set environment variables using the OpenStack RC file]https://docs.openstack.org/ocata/user-guide/common/cli-set-environment-variables-using-openstack-rc.html) each time issuing nova command
