# Ansible Windows Lab

This project contains Ansible playbooks for managing a Windows host. The playbooks can be run individually or together through `win_manage.yml`.

## Playbooks

| File | Purpose |
|---|---|
| `windows_updates.yml` | Searches for and installs Windows updates, rebooting when required. |
| `install_applications.yml` | Downloads and installs Firefox if it is not already installed, then checks for its executable. |
| `configure_windows.yml` | Configures inbound Windows Firewall rules for TCP and UDP port 3389. |
| `manage_services.yml` | Restarts the Print Spooler service and verifies that it is running. |
| `win_manage.yml` | Runs the update, application installation, firewall, and service playbooks in sequence. |

## Inventory

`inventory.ini` defines the Windows host and its WinRM connection settings. Update the inventory to match the Windows host and connection details for your environment.

The current inventory uses WinRM over NTLM on port 5985 and disables server certificate validation. Use connection settings appropriate for your environment.

## Running the playbooks

Run the combined playbook from this directory:

```shell
ansible-playbook -i inventory.ini win_manage.yml