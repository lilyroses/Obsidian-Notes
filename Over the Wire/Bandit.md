# Bandit
#bandit #overthewire #wargames #bash 

---

## Table of Contents

- [[#Setup|Setup]]
	- [[#Setup#Setting up SSH|Setting up SSH]]
		- [[#Setting up SSH#Create SSH Config file|Create SSH Config file]]
		- [[#Setting up SSH#Add Settings to the SSH Config File|Add Settings to the SSH Config File]]
		- [[#Setting up SSH#Test the SSH Config File by Logging In to Level 0|Test the SSH Config File by Logging In to Level 0]]
	- [[#Setup#Setting up a Password File|Setting up a Password File]]
	- [[#Setup#Setting up the Clipboard|Setting up the Clipboard]]
- [[#Levels|Levels]]

---
## Setup 

- [[#Setting up SSH|Setting up SSH]]
	- [[#Setting up SSH#Create SSH Config file|Create SSH Config file]]
	- [[#Setting up SSH#Add Settings to the SSH Config File|Add Settings to the SSH Config File]]
	- [[#Setting up SSH#Test the SSH Config File by Logging In to Level 0|Test the SSH Config File by Logging In to Level 0]]
- [[#Setting up a Password File|Setting up a Password File]]
- [[#Setting up the Clipboard|Setting up the Clipboard]]


---

### Setting up SSH 

- [[#Create SSH Config file|Create SSH Config file]]
- [[#Add Settings to the SSH Config File|Add Settings to the SSH Config File]]
- [[#Test the SSH Config File by Logging In to Level 0|Test the SSH Config File by Logging In to Level 0]]

---

#### Create SSH Config file

```bash
$ mkdir -p ~/.ssh && chmod 700 ~/.ssh
```

```bash
$ touch ~/.ssh/config
$ chmod 600 ~/.ssh/config
```

---

#### Add Settings to the SSH Config File

The following information is given on OverTheWire's Bandit [homepage](https://overthewire.org/wargames/bandit/bandit0.html),

- **Host:** `bandit.labs.overthewire.org`
- **Username:** `bandit[n]`
- **Port:** 2220

For each level. the **username** changes accordingly:

- Level 0: `bandit0`
- Level 1: `bandit1`
	- etc.

Due to the variable nature of the username, we can adjust for this in the `~/.ssh/config` file by using the variable syntax, `"$1"` (`bandit"$1"`). 

This will allow us to use any number after the word `bandit` to log in to the level with our crafted username (if it is a valid username for that level).

We can also use a "shortcut" by setting an arbitrary value (here, I have chosen `otw`) as the **Host**, which we can use in place of our **Hostname** (`bandit.labs.overthewire.org`).

To create this settings file, open `~/.ssh/config` with a text editor (here, I am using `nano`) and add the following text.

```bash
$ nano ~/.ssh/config
```

Add the following text exactly as it appears to the `~/.ssh/config` file. The second, third, and fourth lines are each preceded by a single `Tab` character.

```bash
# Add this text to the ~/.ssh/config file
Host otw
	Hostname bandit.labs.overthewire.org
	User bandit"$1"
	Port 2220
```

Exit and save with:
- `Ctrl` + `x` (exit)
- `y` ('yes' to save)
- `Enter` (close file)

Now, instead of logging in with the following SSH command:

```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220
```

We can log in with a much simpler command:

```bash
# Login for level 0
$ ssh bandit0@otw
```

And for each level thereafter:

```bash
$ ssh bandit1@otw
```

etc.

---

#### Test the SSH Config File by Logging In to Level 0

Test that the SSH config file settings are properly implemented by attempting to log in to level 0:

```bash
$ ssh bandit0@overthewire.org
```

Type `yes` when prompted to accept the 'fingerprint'.

When prompted for the password, type `bandit0`.

Note that no indication of text entry will appear on the screen when typing in the password.

Simply hit `Enter` when done to submit the password.

---

### Setting up a Password File

To save the passwords for each level, we will create a `passwds.txt` file within a the `otw/bandit` directory we will create.

This passwords file will contain first the name of the level (e.g. `bandit0`), a tab character, and then the password for that level.

We will keep track of the passwords in this way because it is highly unlikely we will be able to solve every level in one sitting.

To create the passwords file, first create the parent directories within a directory of your choice (I am working in my `/home/lilyroses` directory).

```bash
$ mkdir -p otw/bandit
```

Within the `bandit` directory you just created, create a blank text file called `passwds.txt`:

```bash
$ touch ~/otw/bandit/passwds.txt
```

Open the `passwds.txt` file and add the first username and password to the file.

```bash
$ nano ~/otw/bandit/passwds.txt
```

The format is as such: 

`username` `tab` `password`

This will be important for later steps, so be sure to use this format, unless you know what you are doing when it comes time to use commands such as `cut`.

```bash
bandit0    bandit0
```

---

### Setting up the Clipboard

---

## Levels 



---