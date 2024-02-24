# Bash
#bash #linux #WSL

---

*See also: [[Shell]]*

---

## System Layout

| Directory | Use | Example Contents |
| ---- | ---- | ---- |
| `/` | Root directory | `/home` |
| `/bin` | System binaries required for sytem to boot/run | `apt`, `nice`, `ls` |
| `/boot` | Contains Linux kernel, initial RAM disk image, and boot loader | - `/boot/grub/grub.conf`, `menu.lst` (to configure boot loader)<br>- `/boot/vmlinuz` (Linux kernel) |
| `/dev` | Device nodes (kernel-recognized devices) | `/dev/block`, `stdin`, `stdout`, `tty`, `tty0` |
| `/etc` | System-wide config (text) files and shell scripts that run at boot time to start system services | - `/etc/crontab` (automated jobs)<br>- `/etc/fstab` (table of storage devices and their mount points)<br>- `/etc/passwd` (user accounts) |
| `/home` | User home directories | `/home/lilyroses` |
| `/lib` | Shared library files used by core system programs. (Similar to `.dll` files in Windows) | `man-db`, `systemd`, `sysctl.d`, `pam.d`, `gcc`, `environment.d` |
| `/lost+found` | Each formatted partition/device that uses a Linux file system (e.g. `ext4`) contains this directory. Used in case of partial recovery from file system corruption. Should be empty unless a big problem happened. | [should be empty] |
| `/media` | Contains mount points for removable media (e.g. USBs, CDs, etc.) | [currently empty] |
| `/mnt` | Contains mount points for removable devices mounted manually (older Linux systems) | On WSL 2, `/mnt` contains `c` (the C drive for Windows) and `wsl` |
| `/opt` | Used to install optional software; e.g. commercial software | [currently empty] |
| `/proc` | Virtual file system maintained by kernel. Text "files" within are for kernel. | `cpuinfo`, `filesystems`, `partitions`, `vmstat`, `uptime` |
| `/root` | Home dir for root account | [currently empty] |
| `/sbin` | "System" binaries. Programs that perform vital tasks, generally reserved for `su` | `hwclock`, `addgroup`, `adduser`, `ownership`, `init`, `chroot`, `cron`, `shadowconfig`, `switchroot`, `sysctl` |
| `/tmp` | Storage of temporary files created by various programs. Some configs empty each time system reboots | [currently empty] |
| `/usr` | Largest directory tree on system. All programs and support files used by regular users | - `/usr/bin` (contains regular user binaries)<br>- `/usr/lib` (shared libraries for programs in `/usr/bin`)<br>- `/usr/sbin` (more sys admin programs)<br>- `/usr/share` (contains all shared data by programs in `/usr/bin`, e.g. default config files, icons, screen backgrounds, sound files, etc.)<br>- `/usr/share/doc` (docs for packages) |
| `/var` | Non-static contents; data stored within is likely to change. Contains various databases, spool files, user mail, etc. | `backups`, `log`, `opt`, `spool`, `mail` |
| `/var/log` | ***Important: Root user should monitor these files from time to time.*** <br>Log files; records of system activity.<br><br>Most important: <br>- `/var/log/messages`<br>- `/var/log/syslog`  | `/var/log/messages` |
|  |  |  |
 

---

## Useful Shortcuts

- [[Bash#Pipe Output to Clipboard|Pipe Output to Clipboard]]

---

### Pipe Output to Clipboard 

When using bash/zsh with WSL 2, you can pipe the output of a command to the clipboard, so that pressing `Ctrl` + `v` pastes the piped command to the terminal. 

The method to do this is a bit different than on a pure Linux system, because the clipboard in question in this situation is the Windows clipboard (`clip.exe`), rather than `xclip` or the like on Linux.

No clipboard tool needs to be installed. Simply use `clip.exe` or write an alias in `~/.bashrc`/`~/.zshrc` to use the `clip` command.

- Add alias for `clip.exe` to `~/.zshrc` (or `~/.bashrc`) to pipe output of command to clipboard and be able to paste back into the WSL terminal with the `Ctrl` + `v`[^1] keyboard shortcut

```bash
$ nano ~/.zshrc


# scroll down to aliases
alias clip='clip.exe'
```

E.g. for [[Over the Wire/Bandit|Bandit]] :

```bash
$ cat passwds.txt | cut -f 2 -d $'\t' passwds.txt | clip.exe
```

---

### Compare Checksum String to Download

- Example: 
	- You download a file, `jdk-21_windows-x64_bin.exe`, to your `Downloads` folder.
	- You copy and paste the `sha256sum` string, provided on the same page as your download link.
	- Open a WSL terminal and use the following format to check the given `sha256sum` string against the calculated hash of the download:

```bash
$ cd /mnt/c/Users/canno/Downloads # to cd into the Downloads directory

$ 
```


[^1]: The normal way to paste in WSL is with `Ctrl` + `Shift` + `v`, but when using the `clip.exe` command, the keyboard shortcut is simply `Ctrl` + `v`.
