# drunkrick (An attempt to "Automate All The Things!" using ansible)

drunkrick tends to eyeball neutrino bombs when he's drunk so... *WARNING* 
most of what lies in this repository contains experimental code used to
create, build and tear down things. It may appear as though I too may have 
been intoxicated whilst putting this together... but I can assure 
you that I probably mostly was...


## Setup macOS 

Theres some things in here I use to setup my 8 year old workstation. Ansible 
does a good job of helping us automate the installation of applications on macOS 
via Homebrew. However, In order to install Homebrew, (or Ansible or Python) we need 
a C compiler. In order to fetch the source, we need git (technically we can download 
this in the form of a tar ball over http). macOS ships a C/C++ compiler and git with 
X Code and even better we don't need to download the whole IDE. We can just grab what 
they call *X Code Command Line Utilities*. 

1. Install X Code Command Line Utilities
       
        xcode-select --install


2. Install Homebrew 

        /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

We can then at this point choose to install ansible via pip Or install a homebrew version of 
python and install ansible via pip. Or install ansible via Homebrew.

3. Install Python 2 (Optional) and sensible

        brew install python@2 python@3 ansible

Ansible pulls in `python@3` from Homebrew anyway so you do not need to include it in the above installation. 
I typed it and can't move the cursor right now, so now I gotta stick with it.

4. At this point I run the macOS.yml playbook to install and setup common applications

        ansible-playbook macOS.yml

The playbook basically loops through a list of applications to install and sets up some preferred user 
settings and dot files.


