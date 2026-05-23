# Ansible

Ansible playbooks for managing infrastructure hosts.

## Setup

Install Ansible:

```sh
pip install ansible
```

Copy the example inventory and add your hosts. The real `inventory.yml`
is gitignored so host details never reach the public repo:

```sh
cp inventory.example.yml inventory.yml
$EDITOR inventory.yml
```

For secrets (passwords, tokens, API keys) use Ansible Vault:

```sh
ansible-vault create group_vars/all/vault.yml
```

`group_vars/` and `host_vars/` are gitignored.

## Usage

Test connectivity:

```sh
ansible-playbook playbooks/ping-hosts.yml
```

Upgrade installed packages on all hosts (reboots only if the host signals one is required):

```sh
ansible-playbook playbooks/upgrade-packages.yml
```

Target a specific host or group:

```sh
ansible-playbook playbooks/upgrade-packages.yml --limit servers
ansible-playbook playbooks/upgrade-packages.yml --limit example
```

Disable automatic reboot:

```sh
ansible-playbook playbooks/upgrade-packages.yml -e reboot_if_required=false
```

## Supported distributions

The `upgrade-packages.yml` playbook handles:

- Debian / Ubuntu (`apt`)
- RHEL / Fedora / Rocky / Alma (`dnf`)
