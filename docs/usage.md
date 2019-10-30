## Playbook example

```yaml
- hosts: your_ec2_servers
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
