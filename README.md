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

Override the variable `repo_host` to specify the location of your local yum repository.

To execute the playbook across my RHEL hosts
```
ansible-playbook -i hosts.rhel packstack.yaml
```

If I only want to enable my locally cached set of base OS RPMS
```
ansible-playbook -i hosts.rhel repos.yaml
```


## Roles

This has been split out into a series of Roles to allow for better re-use

* common - Standard Yum configuration requirements
* local_openstack_repo - Cached OpenStack specific repositories
* local_repo - Cached Base OS Repositories
* openstack_repo - Add the standard RH OSP or RDO Repositories
* packstack - install and run packstack

## Configuration Files / Templates
These contain the local yum repositories config files to reduce internet traffic.

* Base RHEL or Centos repositories - under roles/local_repo/templates
  * centos.repo.j2
  * rhel.repo.j2
* Red Hat OpenStack or RDO repositories - under roles/local_openstack_repo/templates
  * centos_rdo.repo.j2
  * rhel_osp.repo.j2

