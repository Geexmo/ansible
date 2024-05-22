# Ansible Playbook for System Setup and Configuration

This Ansible playbook performs various setup and configuration tasks on a Linux system, including installing packages, formatting and encrypting disks, managing CPU power profiles, renaming network interfaces.

## Requirements

- Ansible 2.9+
- Target system should be running a Linux distribution (tested on Ubuntu)
- Sudo privileges on the target system

## Playbook Tasks

1. Install common packages (`cryptsetup`, `power-profiles-daemon`)
2. Format and encrypt the second disk with LUKS
3. Open the encrypted disk and create an ext4 filesystem on it
4. Encrypt and format the root adjacent partition with LUKS
5. Disable CPU C-states and update GRUB
6. Set and verify the CPU power profile to "balanced"
7. Rename the active network interface to `net0` and display its information
8. Gather and display detailed CPU information

## Usage
Set correct ssh key in hosts
ansible_ssh_private_key_file

There is one external role named common.

To run this playbook, execute the following command:

```sh
ansible-galaxy install -r requirements.yml
ansible-playbook playbooks/play_common.yml -i inventory
