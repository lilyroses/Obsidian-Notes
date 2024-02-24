# WSL 2
#wsl #windows #terminal #ubuntu

---

## Setup WSL 2 on Windows 11

1. Enable WSL 2 for Windows 11
2. Install WSL 2 on Windows 11


---

### Enable WSL 2 for Windows 11

- Open PowerShell

- Enable the optional feature for Windows Subsystem for Linux

```powershell
PS C:\Users\lilyrose> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

- In the Search bar, type 'Enable optional features' and open the first app that appears

- Search the list for 'Virtualization' and make sure the box is checked

- Restart PC

---

### Install WSL 2 on Windows 11

- Open PowerShell

```powershell
PS C:\Users\lilyroses> wsl.exe --install
```

- Restart PC and reopen PowerShell

- Pick a distro to install by listing all available distros
	- *(Note that Ubuntu installs Ubuntu-22.04)*

```powershell
PS C:\Users\lilyroses> wsl.exe --list --online

The following is a list of valid distributions that can be installed.
Install using 'wsl --install -d <Distro>'.

NAME                                   FRIENDLY NAME
Ubuntu                                 Ubuntu
Debian                                 Debian GNU/Linux
kali-linux                             Kali Linux Rolling
Ubuntu-18.04                           Ubuntu 18.04 LTS
Ubuntu-20.04                           Ubuntu-20.04 LTS
Ubuntu-22.04                           Ubuntu-22.04 LTS
OracleLinux_7_9                        Oracle Linux 7.9
OracleLinux_8_7                        Oracle Linux 8.7
OracleLinux9_1                         Oracle Linux 9.1
openSUSE-Leap-15.5                     openSUSE Leap 15.5
SUSE-Linux-Enterprise-Server-15-SP4    SUSE Linux Enterprise Server 15 SP4
SUSE-Linux-Enterprise-15-SP5           SUSE Linux Enterprise 15 SP5
openSUSE-Tumbleweed                    openSUSE Tumbleweed
```

- Install the distro of your choice

```powershell
PS C:\Users\lilyrose> wsl.exe --install -d <Distro>
```

- Restart PC

---

### Setup WSL for the First Time

- Create a username and password

- Update and upgrade the distro 

```bash
$ sudo apt-get update && sudo apt-get upgrade -y
```

- Install basic packages

```bash
$ sudo apt-get install -y [pkg]
```

- Common packages:
	- `zsh`
	- `git`
	- `openvpn`
	- `nano`
	- `code`
	- `python3`
	- `python-is-python3`
	- `pip`
	- `tree`

---

### Setup ZSH, ohmyzsh and powerlevel10k

