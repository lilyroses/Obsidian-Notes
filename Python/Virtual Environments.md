# Virtual Environments
#python #venv #coding

---

## About

- [[#What is a Virtual Environment?|What is a Virtual Environment?]]
- [[#Why Are Virtual Environments Used?|Why Are Virtual Environments Used?]]
- [[#When Should I Use a Virtual Environment?|When Should I Use a Virtual Environment?]]
- [[#Which Virtual Environment Package Should I Use?|Which Virtual Environment Package Should I Use?]]
- [[#How Do I Create a New Virtual Environment?|How Do I Create a New Virtual Environment?]]

---

### What is a Virtual Environment?

- **Virtual Environment:**
	- An isolated space to create Python projects with their own isolated libraries and dependencies
	- Created atop a Python installation (the environment's *base* Python)

---

### Why Are Virtual Environments Used?

**Example Scenario:**

- You have two web-based Python projects, and both use Django.
- One project uses Django 4.0, and the other project uses Django 4.1.
- Creating a virtual environment for each project allows you to have different versions of Django used for each project.

---

### Who Should Use Virtual Environments?

Every Python developer should use virtual environments to manage their Python code projects.

---

### When Should I Use a Virtual Environment?

A new virtual environment should be created for *each Python project*.

---

### Which Virtual Environment Package Should I Use?

`venv`.

Python 3 comes with `venv` pre-installed.

For WSL, I had to run `sudo apt-get install python3.10-venv`.

---
### How Do I Create a New Virtual Environment?

See [[Virtual Environments#Creating a Virtual Environment|Creating a Virtual Environment]] below.

---

## Using a Virtual Environment 

---

### Creating a Virtual Environment

- Use the `venv` command to create a new virtual environment.

In the following example, I create a new virtual environment within my `Seinfeld-Daily-Quote-App` project's root directory:

```bash
$ cd Seinfeld-Daily-Quote-App
$ python3 -m venv ./.venv
```

---

#### Creating a Virtual Environment within an Existing Python Project

To create a virtual environment within an existing Python project, you need to perform the following steps:

1. Create but *do not activate* a new virtual environment within your project's root directory:

```bash
$ cd Seinfeld-Daily-Quote-App
$ python -m venv .venv
```

2. Install the packages required for your project (the Python packages you have already installed with either `pip` or `apt-get`). You can do this by first creating a `requirements.txt` file:

```bash
$ pip freeze > requirements.txt
```

3. Next, edit the `requirements.txt` file and remove any packages that you did not explicitly install.

4. Now, activate your virtual environment:

```bash
$ source .venv/bin/activate
```

5. Install the packages from your `requirements.txt` file:

```bash
$ pip install -r requirements.txt
```

---

### Activating a Virtual Environment

To activate your virtual environment, use the following command *(assume the same location as above)*:

```bash
$ source .venv/bin/activate
```

To deactivate, simply type:

```bash
$ deactivate
```

---

## Conventions

- Do not check your virtual environment into VCS software, such as [[GitHub]].

- Do not place any project code in the virtual environment.

- Should be simple to delete/recreate from scratch - although is not movable or copyable (just recreate the same environment in the [[Virtual Environments#Location of Virtual Environments within Filesystem|target location]]).

---

### Location of Virtual Environments within Filesystem

- By convention, virtual environments are named `venv` or `.venv` in the **project's root directory**[^1]

- You can also keep your virtual environment within a container directory where all your virtual environments are stored, such as `~/.virtualenvs`


[^1]: This is my preferred method.