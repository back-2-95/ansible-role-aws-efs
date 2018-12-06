# Ansible Role: AWS EFS

Role to mount EFS filesystems to EC2 instances.

## Galaxy link

https://galaxy.ansible.com/thiagoalmeidasa/aws-efs/

## Requirements

Amazon AWS account, EFS filesystem(s) and EC2 virtual server(s) with Ubuntu or RedHat.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    aws_efs_paths:
    - { path: "/some/path", owner: "root", group: "root", mode: "0644", region: "eu-west-1", filesystem_id: "fs-someid", state: "mounted", opts: "nfsvers=4.1"}
    - { path: "/some/other/path", owner: "root", group: "root", mode: "0755", region: "eu-west-1", filesystem_id: "fs-someotherid", state: "mounted", opts: "nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2"}

## Dependencies

None.

## Used in requirements.yml

    - src: https://github.com/thiagoalmeidasa/ansible-role-aws-efs
      version: master
      name: thiagoalmeidasa.aws-efs

## Example Playbook

    - hosts: your_ec2_servers
      vars_files:
        - vars/main.yml
      roles:
        - { role: thiagoalmeidasa.aws-efs }

## License

MIT / BSD

## Author Information

This role was created in 2018 by Thiago Almeida.
