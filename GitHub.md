# GitHub

---

## Instructions

You want to...

| You Want To ... | See Here |
| ---- | ---- |
| Set global configuration settings for Git | [[GitHub#Set Global Configuration Settings for Git via Command Line\|here]] |
| Set up an SSH key for GitHub commit authentication | [[GitHub#Set Up SSH Key for Commit Authentication\|here]] |
| Create a new GitHub repository from scratch | [[GitHub#Create a New Empty GitHub Repository\|here]] |
| Create a GitHub repository from an existing, locally hosted code project | [[GitHub#Add Locally Hosted Code to GitHub\|here]] |

1. **Set up Git for development on your laptop:**
	- Set global configuration settings for Git --> see [[GitHub#Set Global Configuration Settings for Git via Command Line|here]]
	- Set up an SSH key for GitHub commit authentication --> see [[GitHub#Set Up SSH Key for Commit Authentication|here]]

2. **Create a GitHub repository:**
	- From scratch --> see [[GitHub#Create a New Empty GitHub Repository|here]]
	- From an existing, locally hosted code project --> see [[GitHub#Add Locally Hosted Code to GitHub|here]]
	- 

---

## Create Repository

---

### Create a New Empty GitHub Repository

1. Create a [[Git#Repository|repository]] (project) using[[GitHub]].

2. [[Git#Clone|Clone]] (copy) the repository to your local machine.

3. [[Git#git add|Add]] (update) files to local repository and [[Git#Commit|commit]] (save) the changes.

4. [[Git#Push|Push]] (update) your changes to the [[Git#Main Branch|main branch]] (main version).

5. Edit your repository on a remote computer, or through GitHub.

6. [[Git#Pull|Pull]] (update) the changes to your local machine.

7. Create a new [[Git#Branch|branch]] (version) of your project, make changes, and commit the changes.

8. Open a [[Git#Pull Request|pull request]] (proposal) for changing to the main branch.

9. [[Git#Merge|Merge]] (update) your branch to the main branch.

---

### Add Locally Hosted Code to GitHub

1. Initialize the Git Repository

2. Open Terminal.

3. Navigate to the root directory of your project:

```bash
	$ cd ~/docs/Obsidian 
```

4. Initialize the local directory as a *local* Git [[Git#Repository|repository]]:

```bash
$ git init -b main
```

5. [[Git#Add|Add]] the files in your new *local* repository to [[Git#Stage|stage]] them for the first [[Git#Commit|commit]].

---

## Set Up Git

---

### Set Up Git with VS Code and Windows 

*Non-WSL*

0. See [[GitHub#Set Up SSH Key for Commit Authentication|here]] for setting up SSH key authentication if you have not already

1. Install the Git extension in VS Code

2. Ensure you are working in a GitHub repository and create a file, then go to the VCS section in the VS Code side bar, and choose "commit changes"

3. Type a commit message in the commit message bar and hit Enter to ensure you are able to commit changes through VS Code. 

---

### Set Global Configuration Settings for Git via Command Line

The commands for PowerShell and bash/zsh are the same.

```bash
$ git config --global USER.NAME "lilyroses"  # Set GitHub username
$ git config --global USER.EMAIL "lilyrosestracke.dev@gmail.com"  # Set GitHub email
```

---

### Set Up SSH Key for Commit Authentication

1. Check for existing SSH key

```bash
$ ls -al ~/.ssh
```

2. Generate a new SSH key

```bash
$ ssh-keygen -t ed25519 -C "lilyrosestracke.dev@gmail.com"
```

3. Set your passphrase when prompted (you will need it when making commits in VS Code)

---

4. Add SSH key to `ssh-agent`

*For LINUX*

```bash
$ eval "$(ssh-agent -s)"
```

```bash
$ ssh-add ~/.ssh/id_ed25519
```

---

*For WINDOWS*

```PowerShell
# Start the ssh agent
PS C:\> Get-Service -Name ssh-agent | Set-Service -StartupType Manual
PS C:\> Start-Service ssh-agent
```

```PowerShell
PS C:\> ssh-add c:/Users/lilyr/.ssh/id_ed25519
```

---

5. Copy SSH public key to clipboard

```bash
# My id_ed25519.pub key 
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIELlGTeJxflUrOu3Y1WxM40C+oRD/O/f3t2jI0HAR0AR lilyrosestracke.dev@gmail.com
```

*For LINUX*

```bash
$ cat ~/.ssh/id_ed25519.pub | clip
```

---

*For WINDOWS*

```bash
PS C:\> cat ~/.ssh/id_ed25519.pub | clip.exe
```

---

6. Navigate to GitHub user settings, and choose `Add SSH Key` under `SSH & GPG Keys`.

7. Add a title describing what device you use the key for (e.g. "Lenovo Small Laptop for WINDOWS Dev"), and paste the PUBLIC key beneath

8. Confirm authentication if prompted.