# Git
#git

---

## Setup Git on a New Computer 

*For Linux/WSL 2 on Windows 10/11*

These instructions are relevant for setting up Git if you:

- Have an existing GitHub account
- Are using a new device or a fresh install of Linux (including WSL 2)
- Do not have an existing SSH key for the device in question

---

### Pre-Requisites

1. Configure git username and email in Linux:

```bash
$ git config --global user.name "lilyroses"
$ git config --global user.email "lilyrosestracke.dev@gmail.com"
```

2. Check that your username and email were set.

```bash
$ git config --global user.name  # lilyroses
$ git config --global user.email # lilyrosestracke.dev@gmail.com
```

---

### Generate an SSH Key Pair

3. Generate a new SSH key to use with your new laptop.

```bash
$ ssh-keygen -t ed25519 -C "lilyrosestracke.dev@gmail.com"
# Hit "Enter" to save in the default location (~/.ssh/ed25519) and type a passphrase.
```

4. Start the ssh-agent in the background.

```bash
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```

Note: For issues with step 4, try one of the following before executing the command in step 4:
- Using root access with `sudo -s -H` *before* starting the ssh-agent
- Using `exec ssh-agent bash` or `exec ssh-agent zsh`

5. Add the SSH private key to the ssh-agent.

```bash
$ ssh-add ~/.ssh/id_ed25519
```

---

### Add the Public SSH Key to GitHub

6. Copy the SSH public key to your keyboard.

```bash
$ cat ~/.ssh/id_ed25519.pub
# ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBKrFpuGVzwXYxoRjDAoIO6ghg6Sqa7cE+CRcL72EoHb lilyrosestracke.dev@gmail.com
```

7. In a browser, navigate to your GitHub account settings and select "SSH and GPG keys", "Add SSH key", and then paste your public key.

---

## Create a New Git Repository

Options:

1. [[Git#Create a Blank Project|Create a Blank Project]]

2. [[Git#Add Git to an Existing Project|Add Git to an Existing Project]]

3. [[Git#Join an Existing Remote Project|Join an Existing Remote Project]]

---

### Create a Blank Project



---

### Add Git to an Existing Project



---

### Join an Existing Remote Project



---

## Clone an Existing Git Repository



---