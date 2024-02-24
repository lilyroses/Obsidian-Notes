# PyInstaller
#python #GUI

---

`pip install PyInstaller`

```ad-attention
***!!! NOTE: if problems packaging apps: update PyInstaller and hooks package***

````python
pip install --upgrade PyInstaller pyinstaller-hooks-contrib
````


---

```ad-example
*example.py*
```Python
import tkinter as tk

window = tk.Tk()
window.title("Hello World")


def handle_button_press(event):
    window.destroy()


button = tk.Button(text="My simple app.")
button.bind("<Button-1>", handle_button_press)
button.pack()

# Start the event loop.
window.mainloop()
```


1. Create windows exe
```python
pyinstaller app.py
```

Creates:

- `build/` : debugging
- ==`dist/`== :
	- `app.exe`
	- binaries and `.dll` files
- `app.spec`

You can take the `dist/` folder and distribute it.

Tweaking the `.spec` file and re-build the app by running `pyinstaller app.spec`

---

