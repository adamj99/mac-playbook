# Mac Playbook

This playbook installs and configures most of the software I use on my Mac for web and software development. Some things in macOS are slightly difficult to automate, so I still have a few manual installation steps, but at least it's all documented here.
## Installation

- Ensure Apple's command line tools are installed (```xcode-select --install``` to launch the installer).

- Ensure Rosetta 2 is installed for M1 Macs (```sudo softwareupdate --install-rosetta``` to launch the installer).

- Install Ansible:
    - Run the following command to add Python 3 to your $PATH: ```export PATH="$HOME/Library/Python/3.8/bin:/opt/homebrew/bin:$PATH"```
    - Upgrade Pip: ```sudo pip3 install --upgrade pip```
    - Install Ansible: ```pip3 install ansible```
        
- Clone or download this repository to your local drive.

- Run ansible-galaxy install -r requirements.yml inside this directory to install required Ansible roles.

- Run ansible-playbook main.yml --ask-become-pass inside this directory. Enter your macOS account password when prompted for the 'BECOME' password.

Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run brew doctor to see if this is the case.

## Options (configured in default.config.yml)
Config | Default | Information
------------ | ------------- | -------------
configure_dock | True | Configures the dock with newly installed packages and removes Apple packages
configure_ssh_key_pair | True | Generates new ssh key pairs (can create multiple)
configure_dotfiles | True | Downloads dot files from remote repos
configure_sudoers | True | Adds a line to sudoers file to stop password prompt
configure_osx | True | Sets up system preferences such as hot corners
