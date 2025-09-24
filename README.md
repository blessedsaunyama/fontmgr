# FontMgr

FontMgr is a Linux font management tool designed to simplify font installation, removal, and organization. It works on Debian-based systems, including Kali Linux, Ubuntu, and Debian, and supports installation via a Cloudsmith repository or manual `.deb` packages.

---

## Table of Contents

1. [Features](#features)
2. [Installation](#installation)
   - [Recommended: Cloudsmith Repository](#recommended-cloudsmith-repository)
   - [Manual `.deb` Installation](#manual-deb-installation)
   - [Direct `dpkg` Installation](#direct-dpkg-installation)
3. [Usage Examples](#usage-examples)
4. [Updating FontMgr](#updating-fontmgr)
5. [Repository Structure](#repository-structure)
6. [Support & Contributions](#support--contributions)

---

## Features

- Install fonts from local files or `.deb` packages
- Remove installed fonts by name
- List all installed fonts
- Update font database
- Supports multiple versions and offline installations
- Works on all Debian-based systems

---

## Installation

### Recommended: Cloudsmith Repository

This ensures you always get the latest stable version and proper dependency handling.

1. Run the Cloudsmith setup script:

```bash
curl -1sLf 'https://dl.cloudsmith.io/public/blessed/fontmgr/setup.deb.sh' | sudo -E bash
````

2. Update your package lists:

```bash
sudo apt update
```

3. Install FontMgr:

```bash
sudo apt install fontmgr
```

4. Verify installation:

```bash
fontmgr --version
```

**Notes:**

* Automatic updates are handled via `apt upgrade`.
* Works for Debian, Ubuntu, Kali Linux, and other derivatives.

---

### Manual `.deb` Installation

1. Download a specific `.deb` version from the repo `debs/` folder:

```bash
wget https://github.com/blessedsaunyama/fontmgr/raw/main/debs/fontmgr-1.0.0.deb
```

2. Install the package with `apt` (recommended, handles dependencies automatically):

```bash
sudo apt install ./fontmgr-1.0.0.deb
```

or with `dpkg`:

```bash
sudo dpkg -i fontmgr-1.0.0.deb
sudo apt -f install
```

3. Verify installation:

```bash
fontmgr --version
```

---

### Direct `dpkg` Installation (Advanced)

For offline installation or local `.deb` files:

```bash
sudo dpkg -i /path/to/fontmgr-<version>.deb
sudo apt -f install   # Fix any missing dependencies
```

* Replace `<version>` with the version number (e.g., `1.0.0`).

---

## Usage Examples

Run `fontmgr --help` to see all commands:

```bash
fontmgr --help
```

### Listing Fonts

```bash
# List all installed fonts
fontmgr list
```

### Installing Fonts

```bash
# Install a single font from local TTF file
fontmgr install /home/user/Downloads/OpenSans.ttf

# Install multiple fonts at once
fontmgr install /home/user/Downloads/*.ttf

# Install a font from a remote URL
fontmgr install https://example.com/fonts/OpenSans.ttf
```

### Removing Fonts

```bash
# Remove a font by exact name
fontmgr remove "Open Sans"

# Remove multiple fonts
fontmgr remove "Open Sans" "Roboto"
```

### Updating the Font Database

```bash
fontmgr update
```

### Advanced Usage

```bash
# List fonts with detailed information
fontmgr list --details

# Check if a font is installed
fontmgr list | grep "Roboto"

# Install fonts system-wide (requires sudo)
sudo fontmgr install /path/to/fonts/*.ttf

# Dry-run installation to see what would happen
fontmgr install --dry-run /path/to/fonts/*.ttf
```

---

## Updating FontMgr

If installed via Cloudsmith repository:

```bash
sudo apt update
sudo apt upgrade fontmgr
```

For manual `.deb` installations:

* Download the new `.deb` version
* Install with `sudo apt install ./fontmgr-<new-version>.deb` or `dpkg`

---

## Repository Structure

```
fontmgr/
├── debs/                  # Contains all .deb package versions
│   ├── fontmgr-1.0.0.deb
│   └── fontmgr-1.1.0.deb
├── README.md              # This file
├── INSTALL.md             # Optional, separate install guide
└── other-docs-or-scripts/
```

* `debs/` folder stores all released versions.
* Users can download specific versions if needed.
* Keep a changelog and update instructions for each version.

---

## Support & Contributions

* GitHub Issues: [https://github.com/blessedsaunyama/fontmgr/issues](https://github.com/blessedsaunyama/fontmgr/issues)
* Email: [saunyamajunior@gmail.com](mailto:saunyamajunior@gmail.com)
* Contributions are welcome via pull requests.
* Star the repo to support the project.

---

**Notes:**

* Cloudsmith repo method is **recommended** for automatic updates and dependency management.
* Manual `.deb` installation is provided for offline or specific version use cases.
* Always check `fontmgr --help` for the latest commands and options.

```
