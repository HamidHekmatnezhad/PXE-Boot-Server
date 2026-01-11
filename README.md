# Multi-OS Automated PXE Deployment Server

This is a **University Project** focused on designing and implementing a fully automated, network-based operating system deployment server within an isolated laboratory environment.

## Project Overview

The goal of this project was to eliminate manual installation processes by creating a "Zero-Touch" deployment system. It supports 5 different Linux distributions using a hybrid architecture of **TFTP** for booting and **HTTP** for high-speed data transfer.

## Key Features

* **Multi-OS Support:** Automated installation for:
* **Debian-based:** Debian 11 & Kali Linux (via *Preseed*)
* **RedHat-based:** Fedora & Rocky Linux (via *Kickstart*)
* **Arch-based:** CachyOS (via *JSON-based Archinstall*)


* **Hybrid Architecture:** Uses **dnsmasq** for DHCP/TFTP and **Nginx** for serving ISO repositories and configuration files.
* **Isolated Environment:** Engineered to work 100% offline using local mirrors and extracted ISO storage.
* **Dynamic Storage:** Implemented a secondary 150GB storage management system to handle multiple high-volume OS images.

## Tech Stack

* **Infrastructure:** Linux (Debian/Ubuntu Server)
* **Services:** `dnsmasq`, `nginx`
* **Automation:** Preseed (cfg), Kickstart (ks), JSON
* **Protocols:** PXE, TFTP, HTTP, DHCP

## Directory Structure

* `/srv/tftp/`: Bootloader, kernels, and initrd files.
* `/var/www/html/`: Local repositories, answer files (Preseed/Kickstart), and OS data.

## Path
```text
.
├── etc
│   ├── dnsmasq.conf
│   └── nginx
│       └── sites-available
│           └── default
├── srv
│   └── tftp
│       ├── os-images
│       │   ├── cachyos
│       │   │   ├── initramfs-linux-cachyos-lts.img
│       │   │   └── vmlinuz-linux-cachyos-lts
│       │   ├── debian
│       │   │   ├── initrd.gz
│       │   │   └── linux
│       │   ├── fedora
│       │   │   ├── initrd.img
│       │   │   └── vmlinuz
│       │   ├── kali
│       │   │   ├── initrd.gz
│       │   │   └── vmlinuz
│       │   └── rocky
│       │       ├── initrd.img
│       │       └── vmlinuz
│       ├── pxelinux.0
│       └── pxelinux.cfg
│           └── default
└── var
    └── www
        └── html
            ├── extract
            │   └── storage
            │       ├── cachyos
            │       │   └── Installationsquelle
            │       ├── debian
            │       │   └── Installationsquelle
            │       ├── fedora
            │       │   └── Installationsquelle
            │       ├── iso
            │       │   └── iso_files
            │       ├── kali
            │       │   └── Installationsquelle
            │       └── rocky
            │           └── Installationsquelle
            ├── cachyos_config.json
            ├── debian_preseed.cfg
            ├── fedora_ks.cfg
            ├── kali_preseed.cfg
            └── rocky_ks.cfg

```