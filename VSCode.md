# VSCode 
#devtools 

---

## Python Development on Windows 11

To use VSCode and Python 3 on Windows 11 (e.g., WITHOUT WSL 2) follow these steps:

- [ ] Download Python from the official Python site
	- [ ] ADD PYTHON TO PATH
- [ ] Install Python extensions from VS Code market

---

### ISSUES

---

#### Issue #1: Python Not Found

==***Status: SOLVED***==

- Ensure Python is installed from official site and added to path, or install from Store
- Ensure interpreter is selected for Python in VS Code
- Reload VS Code

---

#### Issue #2: No Formatter Found for Python

==***Status: SOLVED***==

- In VS Code, open ***USER*** JSON settings
- Add the following to your code  (there should already be a section for Python, `Ctrl` + `F` to find)

*This is for the black formatter*
```json
"[python]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "ms-python.black-formatter"
}
```