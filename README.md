# playbooks

Ansible playbooks for setting up new workstations. Primarily intended for Windows and WSL usage.

**Goals**

- Install Windows desktop applications (via winget or msstore)
- Install Windows CLI applications
- Install WSL
- Configure WSL
- Install Linux CLI applications
- Configure Windows applications

## Prerequisites

- [Windows Package Manager (winget)](https://learn.microsoft.com/en-us/windows/package-manager/)
- Virtualization enabled in Windows host

## Installing WSL

Ansible isn't natively supported on Windows (see [here](https://docs.ansible.com/ansible/latest/os_guide/windows_faq.html#can-ansible-run-on-windows)).

As such, it will need to be installed via Windows Subsystem for Linux (WSL) instead.

From a terminal window (either command prompt or powershell):

```sh
wsl --install
```

This requires elevation so you'll be prompted to provide admin consent for installation to begin. The default distribution is Ubuntu. A different distribution can be specified by using the `-d` argument. For example, run `wsl --install -d Debian` to install Debian.

It can take some time to complete and will require a reboot once done.

To configure WSL, run `wsl` from your terminal. You should be prompted to complete the setup of WSL.

## Installing Ansible

In order to use these playbooks, Ansible will need to be installed manually prior to execution.

### Install pipx

Ansible is distributed via the Python package manager (pip) so first, install pipx via WSL:

```sh
sudo apt update
sudo apt install pipx -y
```

### Intall Ansible Core

Ansible Core is a minimal distribution of Ansible containing only the minimum required libraries and a set of some built-ins.

```sh
pipx install ansible-core
```

Verify the installation

```sh
ansible --version
ansible-playbook --version
```

## References

- [Microsoft Learn: How to install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)