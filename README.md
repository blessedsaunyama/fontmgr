# FontMgr

FontMgr is a tool to manage fonts on Linux systems, designed to simplify font installation, removal, and organization. This repository provides both manual `.deb` packages for Debian-based distributions and instructions to install via our Cloudsmith repository.

---

## Table of Contents
1. [Installation](#installation)
   - [Recommended: Cloudsmith Repository](#recommended-cloudsmith-repository)
   - [Manual `.deb` Installation](#manual-deb-installation)
   - [Direct `dpkg` Installation](#direct-dpkg-installation)
2. [Usage](#usage)
3. [Updating FontMgr](#updating-fontmgr)
4. [Repository Structure](#repository-structure)
5. [Contact / Support](#contact--support)

---

## Installation

### Recommended: Cloudsmith Repository

This method ensures you always get the latest stable version of FontMgr and its dependencies.

1. Add the repository setup script and run it:

```bash
curl -1sLf 'https://dl.cloudsmith.io/public/blessed/fontmgr/setup.deb.sh' | sudo -E bash
Update your package lists:

bash
Copy code
sudo apt update
Install FontMgr:

bash
Copy code
sudo apt install fontmgr
Verify installation:

bash
Copy code
fontmgr --version
Notes:

This method keeps your FontMgr installation up-to-date via apt upgrade.

Works on all Debian-based distributions, including Kali Linux, Ubuntu, Debian, and derivatives.

Manual .deb Installation
If you want to manually install a specific version:

Download the .deb package from this repository’s debs/ folder:

bash
Copy code
wget https://github.com/blessedsaunyama/fontmgr/raw/main/debs/fontmgr-1.0.0.deb
Install the package using apt (handles dependencies automatically):

bash
Copy code
sudo apt install ./fontmgr-1.0.0.deb
or using dpkg (you may need to fix dependencies manually):

bash
Copy code
sudo dpkg -i fontmgr-1.0.0.deb
sudo apt -f install
Verify installation:

bash
Copy code
fontmgr --version
Direct dpkg Installation (Advanced)
If you already have a .deb file:

bash
Copy code
sudo dpkg -i /path/to/fontmgr-<version>.deb
sudo apt -f install   # Fix any missing dependencies
Replace <version> with the version number (e.g., 1.0.0).

Works for offline installations if you distribute the .deb file.

Usage
Run the following to see available commands:

bash
Copy code
fontmgr --help
Example commands:

bash
Copy code
# List all installed fonts
fontmgr list

# Install a font from a local file
fontmgr install /path/to/font.ttf

# Remove a font by name
fontmgr remove "Open Sans"

# Update font database
fontmgr update
Updating FontMgr
If you installed via Cloudsmith repository:

bash
Copy code
sudo apt update
sudo apt upgrade fontmgr
For manual .deb installations:

Download the new .deb version from the repo

Install using sudo apt install ./fontmgr-<new-version>.deb

Repository Structure
bash
Copy code
fontmgr/
├── debs/                  # Contains all .deb package versions
│   ├── fontmgr-1.0.0.deb
│   └── fontmgr-1.1.0.deb
├── README.md              # This file
└── other-docs-or-files/
The debs/ folder stores all published versions.

Users can download specific versions if needed.

Contact / Support
For issues, suggestions, or contributions:

GitHub Issues: https://github.com/blessedsaunyama/fontmgr/issues

Email: saunyamajunior@gmail.com

Note: Installing via Cloudsmith repository is recommended for automatic updates and proper dependency handling. Manual .deb installation is available for offline or specific version needs.
