# drunkrick

drunkrick tends to eyeball neutrino bombs when he's drunk so... *WARNING* 

This repository contains **Ansible playbooks** designed to automate the installation of 
essential software on macOS via Homebrew.

## Disclaimer
**This is a personal "build-for-purpose" tool.** It is specifically tailored to my professional workflow 
and does not handle dotfiles, symlinks, or deep system configuration. It is intended to serve as a fast 
"software checklist" for fresh macOS installs.

**Feel free to fork this repository** and customize the package lists to suit your own needs.

---

## What's Inside?

The playbook automates the installation of two categories of software:

### 1. Homebrew Formulae (CLI Tools)
* **Infrastructure:** Ansible, Terraform, Terragrunt, AWS CLI.
* **Database:** `pgcli`, `mycli`, Pocketbase.
* **Runtimes:** Go, UV (Python), NVM (Node), jEnv (Java).
* **Networking/Security:** Nmap, OpenFortiVPN, `ssh-copy-id`.
* **PDE:** Neovim.

### 2. Homebrew Casks (GUI Applications)
* **Browsers:** Firefox, Google Chrome.
* **Editors:** JetBrains Toolbox, VS Code, Kitty (Terminal).
* **AI Editors:** Trae, Windsurf, Antigravity.
* **Admin/Tools:** Docker Desktop, DBeaver, Postman, Leapp.
* **Office:** Microsoft Office.

**Note on Permissions:** *Homebrew forbids running directly as sudo. We use --ask-become-pass because certain GUI applications (Casks like Microsoft Office) require administrative privileges to write to the /Applications folder. Ansible handles this by running Homebrew as your user and only escalating for the system-level installer components.*



## Getting Started

### Prerequisites:

Before running the playbook, you must manually install the foundational tools:

#### 1. Xcode Command Line Tools:
   Open your terminal and run:
   ```bash
   xcode-select --install
   ```

A software update popup will appear; click "Install" and wait for it to finish.

#### 2. Homebrew:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```


#### 3. Ansible:

```bash
brew install ansible
```

### Installation:

Clone your fork of this repository:

```bash
git clone https://github.com/imesias/drunkrick.git
cd drunkrick
```

Run the playbook:

```bash
ansible-playbook macOS.yml --ask-become-pass
```

**Note:** --ask-become-pass is required for tasks that may need sudo privileges (like certain Cask installs).

### Post-Installation (Manual Setup)
This playbook focuses on provisioning, not configuration. I may add configuration later.
After the run completes, you are expected to perform your own manual post-configuration:

* **Cloud/Auth:** Sign in to browsers, Docker, and Leapp. 
* **Security:** Generate and add your SSH keys.
* **Runtimes:** Initialize your environments (e.g., nvm install --lts, jenv add ...).
* **Dotfiles:** Manually source or symlink your .bashrc and .bash_prompt.


### Contributing:
If you have suggestions for improvements or would like to start adding configs to avoid post configuration.
feel free to open a PR. Otherwise, please fork and adapt! `
