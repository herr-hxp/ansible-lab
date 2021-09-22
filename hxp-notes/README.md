Run this in the folder where you want to clone the repo

### Lab
## System Overview
# Control Node
# Common network: labnet.io
# 4 Managed nodes (ubuntu-[a-c])
# ---
# Shared disk
# ssh folder with subfolders for each system with keys
# ports, 80 8080
# ---
# Run playbooks and commands from Control Node

## Getting started
# Download the repo
#git clone https://github.com/MagnusLarsson001/ansible-lab.git
#git clone git@github.com:MagnusLarsson01/ansible-lab.git
git clone git@github.com:herr-hxp/ansible-lab.git
# Create dirs
mkdir -p $HOME/ansible-lab/shared
mkdir -p $HOME/ansible-lab/ssh/control_node
mkdir -p $HOME/ansible-lab/ssh/ubuntu-{a..d}
# Change apt to apt-get in ubuntu/dockerfile

## Start the docker-compose services (first time: --build)
# docker-compose up -d --build
# Ensure that the services are running
# docker ps
# Start an interactive shell with the control node
# docker exec -it controlnode /bin/bash
# ---
# Ensure that you use the ansible user
# if [[ ! "$(whoami)" == "ansible" ]]; then
#   su ansible
# fi
# ---
# Now you're ready to run
#+ Use the shared folder to enter files such as inventories and playbooks
#+ The shared folder in $HOME/ansible-lab/shared is mounted on /shared in the controlnode container
# ---
# Create ssh keys
# ssh-keygen
# Copy the keys to all hosts
# ssh-copy-id ubuntu-a.labnet.io
# ssh-copy-id ubuntu-b.labnet.io
# ssh-copy-id ubuntu-c.labnet.io
# ssh-copy-id ubuntu-d.labnet.io
# The password is password1

## Validate the environment
# This should return the hostnames of all hosts
# ansible all -m command -a "hostname"
# You're READY

