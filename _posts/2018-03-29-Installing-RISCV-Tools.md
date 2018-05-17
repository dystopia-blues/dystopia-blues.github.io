---
title: Installing the RISC-V Tools
tags: [ RISC-V, Assembly ]
---

## Installing the RISC-V Tools
The following instructionsa will copy the github repos to your home directory `~` and install them under `/opt/riscv/bin`.

### Use home directory for github sources
```
cd ~
```
### Clone and update refs
```
git clone https://github.com/riscv/riscv-tools.git
cd riscv-tools/
git submodule update --init --recursive
```
### Install in to /opt
```
sudo mkdir /opt/riscv
```
### Set required variables
```
export RISCV=/opt/riscv
export PATH=$PATH:/opt/riscv
export TOP=/opt
```
### Run build script
```
sudo -E ./build.sh
```
### Update path
```
echo export PATH=\$PATH:/opt/riscv/bin >> ~/.bashrc
```
