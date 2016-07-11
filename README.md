# Ansible Role: AWS EFS

Role to mount EFS filesystems to EC2 instances.

## Requirements

Amazon AWS account, EFS filesystem(s) and EC2 virtual server(s) with Ubuntu or RedHat.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    aws_efs_paths:
    - { path: "/some/path", owner: "root", group: "root", mode: "0644", region: "eu-west-1", filesystem_id: "fs-someid"}
    - { path: "/some/other/path", owner: "root", group: "root", mode: "0755", region: "eu-west-1", filesystem_id: "fs-someotherid"}

## Dependencies

None.

## Example Playbook

    - hosts: your_ec2_servers
      vars_files:
        - vars/main.yml
      roles:
        - { role: back-2-95.aws-efs }

## License

MIT / BSD

## Author Information

This role was created in 2016 by Marko Korhonen.
