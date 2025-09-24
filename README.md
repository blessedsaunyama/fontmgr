# FontMgr

![FontMgr](https://img.shields.io/badge/fontmgr-1.0.0-blue.svg)  
**Font Manager Utility** – Manage local and online fonts on Linux easily.  
Author: Blessed Tanaka Saunyama

---

## Overview

`FontMgr` is a command-line utility for installing, managing, and removing fonts.  
It supports both local font files and downloading fonts from online sources, with optional variant selection.

---

## Installation

You can install `fontmgr` using several methods:

### 1. Cloudsmith (Recommended)

Cloudsmith hosts your `.deb` packages and allows easy APT integration.

```bash
# Run setup script to add repository
curl -1sLf 'https://dl.cloudsmith.io/public/blessed/fontmgr/setup.deb.sh' | sudo -E bash

# Update package list
sudo apt update

# Install fontmgr
sudo apt install fontmgr
````

### 2. GitHub Raw `.deb` Download

You can download the `.deb` directly from GitHub:

```bash
# Download the package
wget https://github.com/blessedsaunyama/fontmgr/raw/main/debs/fontmgr-1.0.0.deb

# Install the package
sudo apt install ./fontmgr-1.0.0.deb
```

> Note: Replace the version number if a newer release is available.

### 3. Local `.deb` Package

If you already have the `.deb` file:

```bash
sudo apt install ./fontmgr-1.0.0.deb
```

### 4. Build from Source (Optional)

Clone the repository and build your own `.deb` using `fpm`:

```bash
git clone https://github.com/blessedsaunyama/fontmgr.git
cd fontmgr
fpm -f -s dir -t deb -n fontmgr -v 1.0.0 .
sudo dpkg -i fontmgr_1.0.0_amd64.deb
```

---

## Usage

```bash
fontmgr [FAMILY[:variants] ...] [options]
```

### Short Examples

```bash
fontmgr                       # Install all fonts in current directory (non-recursive)
fontmgr -R                    # Install all fonts in current directory and subfolders
fontmgr Roboto                # Download all Roboto variants from configured online sources
fontmgr "Roboto:Bold,Italic"  # Download only Bold and Italic variants of Roboto
fontmgr -d ~/Fonts            # Install fonts from ~/Fonts (non-recursive)
```

---

### Options

| Option                        | Description                                                                             | Example                                           |                                                                     |
| ----------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------------------------- |
| `-R, --recursive [DIR]`       | Install fonts recursively (default DIR=`.`)                                             | `fontmgr -R ~/Downloads/Fonts`                    |                                                                     |
| `-d, --dir DIR`               | Install fonts from DIR only (non-recursive)                                             | `fontmgr -d ~/Fonts`                              |                                                                     |
| `-o, --online [FAMILY...]`    | Install online families. Accepts multiple families or quoted `"Family:Variant,Variant"` | `fontmgr -o Roboto "OpenSans:Bold,Italic"`        |                                                                     |
| `-u, --url URL`               | Install a font directly from a URL (single file)                                        | `fontmgr -u https://example.com/fonts/MyFont.ttf` |                                                                     |
| `-r, --remove NAME[:VARIANT]` | Remove a font family or specific variant                                                | `fontmgr -r Roboto:Bold`                          |                                                                     |
| `--list-sources`              | List configured online sources                                                          | `fontmgr --list-sources`                          |                                                                     |
| `--add-source NAME TYPE URL`  | Add a new online source (\`type=github                                                  | direct\`)                                         | `fontmgr --add-source MyFonts github https://github.com/user/fonts` |
| `--remove-source NAME`        | Remove a configured source by name                                                      | `fontmgr --remove-source MyFonts`                 |                                                                     |
| `-l, --list`                  | List installed font families                                                            | `fontmgr -l`                                      |                                                                     |
| `-v, --variants FAMILY`       | List tracked variants for FAMILY                                                        | `fontmgr -v Roboto`                               |                                                                     |
| `--refresh`                   | Refresh font cache                                                                      | `fontmgr --refresh`                               |                                                                     |
| `--about`                     | Show about info                                                                         | `fontmgr --about`                                 |                                                                     |
| `-h, --help`                  | Show this help and exit                                                                 | `fontmgr --help`                                  |                                                                     |
| `--version`                   | Show version and exit                                                                   | `fontmgr --version`                               |                                                                     |

---

### Notes & Tips

* Typing `fontmgr` with **no arguments** installs all font files in the current directory (non-recursive).
* Bare words (no dash) are treated as **online family names** to download.
* You can **combine local installs** (`-d` or `-R`) and **online families** in a single command:

```bash
fontmgr -R -o Roboto "OpenSans:Bold,Italic" ~/MyFonts
```

* **Remove fonts selectively**:

```bash
fontmgr -r Roboto           # Remove entire Roboto family
fontmgr -r "Roboto:Bold"    # Remove only Bold variant
```

* **Manage online sources**:

```bash
fontmgr --add-source MyRepo github https://github.com/user/fonts
fontmgr --remove-source MyRepo
fontmgr --list-sources
```

* **Check installed fonts and variants**:

```bash
fontmgr -l                     # List all installed font families
fontmgr -v Roboto               # List all variants tracked for Roboto
```

---

## License

MIT License – see `LICENSE` file for details.

---

## Contributions

Contributions, bug reports, and feature requests are welcome!

* Fork the repository
* Create a branch for your feature/bugfix
* Open a pull request with a clear description

---

## References

* [Cloudsmith Documentation](https://cloudsmith.com/docs)
* [GitHub Releases](https://github.com/blessedsaunyama/fontmgr/releases)
* [FontMgr Issues](https://github.com/blessedsaunyama/fontmgr/issues)

```
Do you want me to do that next?
```
