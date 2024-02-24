# Vagrant
#virtualization

---

## About

- **Vagrant** is a tool to **automate** the **creation** and **management** of development environments, (usu. with **virtual machines**)

- **Isolate** software **dependencies** and **configurations** within a single, **disposable**, consistent environment

- Allows any software to **"just work"** on **any system**

- Works with [[VirtualBox]]


---

## Setup

Setup a virtual machine with Ubuntu 18.04 LTS 64-bit.

---

### Initialize Vagrant

```sh
$ vagrant init hashicorp/bionic64
```

```sh
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```

Ensure Vagrant has created a `Vagrantfile`. This configures the deployment for the virtual machine.

For more information on the `Vagrantfile`, see [[Vagrant#Vagrantfile|here]].

```sh
$ ls -la
```

---

### Start Ubuntu VM

```sh
$ vagrant up
```

When the VM is deployed, messages will appear stating that the VM is booted.

```sh
==> default: Machine booted and ready!
==> default: Configuring network adapters within the VM...
==> default: Waiting for HGFS to become available...
==> default: Enabling and configuring shared folders...
```

Connect to the machine with `vagrant ssh` and explore the environment.

Leave the `ssh` session with `logout`.

---

### Destroying the VM

When done, terminate the VM.

```sh
$ vagrant destroy  # confirm with y
```

---

## Vagrantfile

To configure any Vagrant project, create a `Vagrantfile`.

This allows you to:

- Mark the **root directory** of your project
- Describe the **machine and resources** needed for your project, and the **software** to install/how to access the software

---