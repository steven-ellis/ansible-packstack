# ansible-packstack
Example Ansible Playbook for Packstack

Aim is to simplify the install of OpenStack via Packstack onto
Red Hat Enterprise Linux 7 and Centos 7 environments

## Driving the playbook

You'll need to specify your inventory `hosts.rhel` file that contains the host you wish to packstack

```
[packstack]
openstack
```

Execute playbook across my RHEL hosts
```
ansible-playbook -i hosts.rhel -v packstack.yaml
```

## Includes
The includes configure the local respositories on the packstack hosts

* local_repo.yaml - Base OS repositories
* local_openstack_repo.yaml - OpenStack specific repositories
 
## Configuration Files
These contain the local yum repositories config files to reduce internet traffic.

* Base RHEL or Centos repositories
  * centos.repo.j2
  * rhel.repo.j2
* Red Hat OpenStack or RDO repositories
  * centos_rdo.repo.j2
  * rhel_osp.repo.j2

