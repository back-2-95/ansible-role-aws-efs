# Ansible Role: AWS EFS

Mount Amazon EFS file systems to EC2 instances.

## Galaxy link

https://galaxy.ansible.com/thiagoalmeidasa/aws_efs/

## Requirements

Amazon AWS account, EFS filesystem(s) and EC2 virtual server(s) with Ubuntu or RedHat.

## Ansible requirements

### Ansible version

Minimum required ansible version is 2.0.

### Ansible role dependencies

None.

## Installation

### Install with Ansible Galaxy

```shell
ansible-galaxy install thiagoalmeidasa.aws_efs
```

Basic usage is:

```yaml
- hosts: all
  roles:
  - role: thiagoalmeidasa.aws_efs
    vars:
      aws_efs_paths:
      - path: "/some/path",
        owner: "root",
        group: "root",
        mode: "0644",
        region: "eu-west-1",
        filesystem_id: "fs-someid",
        state: "mounted",
        opts: "nfsvers=4.1"
      - path: "/some/other/path",
        owner: "root",
        group: "root",
        mode: "0755",
        region: "eu-west-1",
        filesystem_id: "fs-someotherid",
        state: "mounted",
        opts: "nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2"
```

### Install with git

If you do not want a global installation, clone it into your `roles_path`.

```shell
git clone git@github.com:thiagoalmeidasa/ansible-role-aws-efs.git /path/to/roles_path
```

But I often add it as a submdule in a given `playbook_dir` repository.

```shell
git submodule add git@github.com:thiagoalmeidasa/ansible-role-aws-efs.git <playbook_dir>/roles/aws_efs
```

As the role is not managed by Ansible Galaxy, you do not have to specify the
github user account.

Basic usage is:

```yaml
- hosts: all
  roles:
  - role: aws_efs
    vars:
      aws_efs_paths:
      - path: "/some/path",
        owner: "root",
        group: "root",
        mode: "0644",
        region: "eu-west-1",
        filesystem_id: "fs-someid",
        state: "mounted",
        opts: "nfsvers=4.1"
      - path: "/some/other/path",
        owner: "root",
        group: "root",
        mode: "0755",
        region: "eu-west-1",
        filesystem_id: "fs-someotherid",
        state: "mounted",
        opts: "nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2"
```

## Role Variables

Variables are divided in three types.

The [default vars](#default-vars) section shows you which variables you may
override in your ansible inventory. As a matter of fact, all variables should
be defined there for explicitness, ease of documentation as well as overall
role manageability.

The [mandatory variables](#mandatory-variables) section contains variables that
for several reasons do not fit into the default variables. As name implies,
they must absolutely be defined in the inventory or else the role will
fail. It is a good thing to avoid reach for these as much as possible and/or
design the role with clear behavior when they're undefined.

The [context variables](#context-variables) are shown in section below hint you
on how runtime context may affects role execution.

### Default vars

Role default variables from `defaults/main.yml`.

```yaml
# Mount mappings
#
# Notes:
# - Filesystem must be in the same security group with the EC2 instances using it
# - For details of Amazon EFS service availability by region, check: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
#
# Options:
# - path:           Local path to mount target folder in your EC2 instance
# - owner:          Owner of the folder (default value "root")
# - group:          Group of the folder (default value "root")
# - mode:           Permissions for the folder (default value "0644")
# - region:         In what region filesystem is
# - filesystem_id:  Filesystem ID
# - state:          Ansible mount module options. (default value "mounted")  http://docs.ansible.com/ansible/latest/mount_module.html#options
# - opts:           Mount options (see fstab(5), or vfstab(4) on Solaris). (default following aws instructions "nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2")

# Mount paths
aws_efs_paths:
  - path: /opt/efs
    owner: ""
    group: ""
    mode: ""
    region: ""
    filesystem_id: ""
    state: ""
    opts: ""
```

### Mandatory variables

```
aws_efs_paths:
- path: ""
  owner: ""
  group: ""
  mode: ""
  region: ""
  filesystem_id: ""
  state: ""
  opts: ""
```

### Context variables

None.

## License

license (BSD, MIT).

## Author Information

thiagoalmeidasa <thiagoalmeidasa@gmail.com>.
