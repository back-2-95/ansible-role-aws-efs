# Ansible Role: AWS EFS

Role to mount EFS filesystems to EC2 instances.

## Requirements

Amazon AWS account, EFS filesystem(s) and EC2 virtual server(s) with Ubuntu or RedHat.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    aws_efs_paths: []

## Dependencies

None.

## Example Playbook

    - hosts: webservers
      vars_files:
        - vars/main.yml
      roles:
        - { role: back-2-95.aws-efs }

## License

MIT / BSD

## Author Information

This role was created in 2016 by Marko Korhonen.