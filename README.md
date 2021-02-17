# rudl-config-template
Configuation template repository

Access Key key_id: test1: testtest


## General

All state and service files are kept in the master branch. It can be protected.
But there should be no dedicated testing branch with real machine interaction


## Hypervisor Provisioning

Install the hard and software.

Run:

```
docker service start rudl/provisioneer
    -e principal=principal.xy.de
    -e class=hv
    -e hv.create_key=123456
    -e hv.state_file=/var/rudl/libvirt.state.json
    -e hv.name=hostname
    -v /:/hostfs
```


## VM Provisioning

Create a new VM. Log into it (or by cloud-config) run the following script

```
docker service start rudl/provisioneer 
    -e principal=principal.xy.de 
    -e class=vm
    -e vm.create_key=1234456
    -e vm.state_file=/var/rudl/vm.state.json
    -e vm.name=someName # Optional - otherways hostname is used
    -v /:/hostfs
```

It will

- Create a `/var/rudl/vm.state.json` file containing private/public key pair for
  communication with the principal. You'll have to remove / re
- 

## Using Groups

Groups make metadata about all members available to the other members of the
stack. (Join-Tokens, Shared secrets, etc)