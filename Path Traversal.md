# Path Traversal
#websec #portswigger

---

## About

- **Path Traversal:** a.k.a. *directory traversal*
	- Read/write to files on server

---

## Example

- Shopping app displays images of items using HTML:

`<img src="/loadImage?filename=218.png">`

- **URL:** `loadImage` 
- **Parameter:** `filename`
- **Requested image file:** `218.png`

- **Base directory:** `/var/www/images/` (default server image storage)
- **Requested image file location:** `/var/www/images/218.png`

`/var/www/images/218.png`


Steps:

1. Image file `218.png` requested through HTML: `<img src="/loadImage?filename=218.png">` 
2. App base image directory: `/var/www/images/`
3. Requested filename appended to base directory: `/var/www/images/218.png`
4. File read w/ filesystem API

---

## Path Traversal Attacks

If no defenses are in place, attacker's can request specially crafted URLs to retrieve, say, the `/etc/passwd` file from the server's filesystem:

`https://insecure-website.com/loadImage?filename=../../../etc/passwd`

(How do we know for sure that the app is querying the `/var/www/images/ path?)

Since we know that the filename is appended to the `/var/www/images/` base directory, we can use this knowledge to travel *up* the filesystem. 

Using the path `../../../etc/password`, therefore, queries the following path:

`/var/www/images/../../../etc/passwd`

Because `/var` is actually the first directory after the filesystem root (`/` = root, `var` = 1 step lower), using 3 `../` sequences means moving *up* three levels.

`/var/www/images/` is **4** levels deep.

- **4th level:** `images/`
- **3rd level:** `www/`
- **2nd level:** `var/`
- **1st level:** `/` (root)

Moving up 3 levels brings us to the filesystem root.

- **Starting directory:** `/var/www/images/` *(4 levels deep)*
- **Move up 1 level:** (`../`) -> `/var/www/` *(3 levels deep)*
- **Move up 2 levels:** (`../../`) -> `/var/` *(2 levels deep)*
- **Move up 3 levels:** (`../../../`) -> `/` *(Root level)*


| Start Path | Traversal | New Path | Level |
| `/var/www/images/`  | `../` | `/var/www/` | 3 |
| `/var/www/images/`  | `../../` | `/var/` | 2 |
| `/var/www/images/` | `../../../` | `/` | 1 |

---

## Labs

---

### Lab 1 - File Path Traversal, Simple Case

To solve, retrieve contents of `/etc/passwd` file

- **Product URL:** https://0ad7009c043d4cc680c3809500e7006a.web-security-academy.net/product?productId=2
	- Note the parameter is `product?productId=2`

- Right-click image file, and choose "Open in new tab"

- When image is opened in new tab, view the new URL: https://0ad7009c043d4cc680c3809500e7006a.web-security-academy.net/image?filename=14.jpg
	- Note the parameter has changed to `image?filename=14.jpg`
	- This gives us an indication that we are reading from the `/var/www/images/` directory

- Remove the filename parameter value of `14.jpg` and replace it with `../../../etc/passwd` to solve the lab.
	- Note that I had no idea the lab was actually solved until I went back to the main store page. *How on earth would I know I was successful in real life?*

For products:
- **URL:** `product`
- **Parameter:** `productId`
- **Requested product:** `2`

For images:
- **URL:** `image`
- **Parameter:** `filename`
- **Requested image:** `14.jpg`
- **Changed to:** `../../../etc/passwd`

---

### Lab 2 - File path traversal, traversal sequences blocked with absolute path bypass

Check the URL of a product's page.

Open the image of the product in a new tab.

Change the filename requested in the URL to `/etc/passwd`.

The lab is solved.

---

## Nested Traversal Sequences

`....//` 

`....\/`

Revert to simple traversal sequences when inner sequence is stripped

- `....//` -> strip `../` -> `../`

- `....\/` -> strip `../` -> `..\` (for Windows)

- **URL encoding:** `../` -> `%2e%2e%2f`

- **Double URL encoding:** `../` -> `%252e%252e%252f`

- **Non-standard encodings:** `../` -> `..%c0%af`

- **Non-standard encodings:** `../` -> `..%ef%bc%8f`

---

### Lab 3 - File Path Traversal, Traversal Sequences Stripped Non-Recursively

To solve, retrieve contents of `/etc/passwd` file.

Click on any product.

Open the image in a new tab.

Remove the filename parameter, and append the following sequence to the URL:

`....//....//....//etc/passwd`

This solves the lab.

`....//....//....//etc/passwd` -> `../../../etc/passwd` after traversal sequences are stripped.

