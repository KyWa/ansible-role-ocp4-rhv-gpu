# OCP4-RHV-GPU

What this Role Does
- Iterate through a list of RHV hosts that have GPUs
- Create new Machines in OpenShift to attach these GPUs to
- Scale and attach GPUs to OpenShift Machines

What this Role Does Not
- Setup a RHV Host with a GPU
- Obtain the ovirt_cluster_id and Ovirt vnic_profile_ids

## Requirements

You will need to handle steps 1-2 in this document https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.4/html/setting_up_an_nvidia_gpu_for_a_virtual_machine_in_red_hat_virtualization/assembly_nvidia_gpu_passthrough, as the Role does not handle this portion. The link will guide you on getting a RHV (oVirt) host setup with a host device to be passed through.

## Role Variables

You will need to obtain information from your RHV (Ovirt) Cluster and update your inventory variables accordingly:

```
ovirt_cluster_id: ""
vnic_profile_id: ""
```

You will also need to update inventory vars for which RHV hosts have GPUs assigned to them:

```
gpu_rhv_hosts:
  - ""
gpu_host_machinesets:
  worker-gpu-01: ""
```

## Dependencies

### Python Modules
ovirt-engine-sdk-python >= 4.4.0

### Ansible Collection (if using non Red Hat subscriber Ansible versions)
`ansible-galaxy collection install ovirt.ovirt`


## Example Playbook

The file `playbook.yml` contains an example playbook that will run this role and you would run it like this:

`ansible-playbook -i hosts playbook.yml`

## License

MIT / BSD
