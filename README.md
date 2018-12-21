# Ansible AWS CLI role

Ansible role to install and configure the aws-cli.

- Tested on Ubuntu 16.04 Server;
- Ansible 2.7+

## Role Variables

The default variables are as follows:

```yaml
aws_cli_user: '{{ ansible_user }}'
aws_cli_group: '{{ ansible_user }}'
aws_output_format: 'json'
aws_region: 'ap-southeast-2'
aws_access_key_id: 'YOUR_ACCESS_KEY_ID'
aws_secret_access_key: 'YOUR_SECRET_ACCESS_KEY'
```

## Example

host_vars/vault_example_vars.yaml (Ideally to be encryed by ansible-vault)

```yaml
---
aws_cli_user: '{{ ansible_user }}'
aws_cli_group: '{{ ansible_user }}'
aws_output_format: 'json'
aws_region: 'ap-southeast-2'
aws_access_key_id: 'YOUR_ACCESS_KEY_ID'
aws_secret_access_key: 'YOUR_SECRET_ACCESS_KEY'
```

example-playbook.yaml

```yaml
---
- hosts: Server
  roles:
    - aws-cli
```

Command to run the playbook

```bash
ansible-playbook -i <inventory-file> -u ubuntu --key-file=<path-to-ssh-key> \
                 -e @./host_vars/vault_example_vars.yaml [--vault-id @prompt] example-playbook.yaml
```

## Reference

[https://github.com/dstil/ansible-aws-cli](https://github.com/dstil/ansible-aws-cli)