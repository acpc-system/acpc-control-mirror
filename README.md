# ACPC Control server local mirror
# Introduction
ACPC system installation based on installing a fresh copy of the OS followed by installing the required IDE, Debuggers, Judging s/w, and other administrative environment. Installing any package needs a configured mirror for downloading the package and its dependencies. The default mirror location is the Internet mirror. Installing simultaneous devices in the same time requires a stable and huge internet bandwidth specially at the required packages installation. Internet access also is not allowed in the contest hall at any time. A local mirror required to speed up the installation process. Creating a local mirror needs a storage, and a syncing process from Internet mirror to the local mirror.

# Why using mirror
As mentioned, eliminates the need for a huge internet bandwidth, and speed up the installation, and update processes.

# What about mirror updates
Also, there is a script to update the local mirror to contains tha newly added packages, remove obsolete one, and update the existing pakcages if any.

# Prerequisites
  1. Ubuntu box
  2. Sufficient space to hold the mirror
  3. python v.3 
  4. ansible
  5. Internet connection
  6. Downloading privileges.
  7. ACPC Control server ansible playbook from https://github.com/acpc-system/acpc-control-ansible
  
# How to install
  * cd ansible
  * git clone https://github.com/acpc-system/acpc-control-mirror

# Usage:
 * cd ansible/acpc-control-mirror
 * sudo ansible-playbook files/mirror.yml 
 
# Customize your playbook.
  The base directory for the playbook environment, is ansible/acpc-control-mirror.
  1. To specify the ubuntu dist, update  roles/mirror/vars/main.yml, and change the value for variable ubuntu_dist. It is bionic by default
  2. To specify the ubuntu architecture, update  roles/mirror/vars/main.yml, and change the value for variable ubuntu_arch. It is i386 by default
  

# How does it work?
The mirror sync is a process of cloning the internet ubuntu mirror to a local storage, which will be typically /MirrorPool in the ACPC Control Server which created before from https://github.com/acpc-system/acpc-control-ansible. By default, it syncs the mirror for the ACPC Control server architecture. If you want to download the mirror for different architecture(s) you have to mention that in the configuration file ansible.cfg

# What is included and what is not included?
The local mirror includes main, restricted, and universe sections of Ubuntu. Does not include security updates, and sources.
