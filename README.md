# Xgui4's FreeBSD Ports Overlay

This repository contains Ports overlay for installing my softwares ports on FreeBSD.

> [!CRITICAL]
> This repo is currently in progress/developpement, so i do not recommend using it right now.

## Prerequisites: Set Up Poudriere & Create a Jail

Before using this overlay, you need a Poudriere jail. Poudriere builds packages inside clean, isolated environments called jails.
More info [on the manual page of poudriere](https://man.freebsd.org/cgi/man.cgi?poudriere)

### 1. Create a Poudriere Jail

Run this command to have Poudriere automatically download, extract, and create a jail (replace `14_1_RELEASE` and `14.1-RELEASE` with your target FreeBSD version):

```bash
poudriere jail -c -j 14_1_RELEASE -v 14.1-RELEASE
```

* `-c`: Creates the jail.
* `-j`: Sets the short name for your jail (e.g., `14_1_RELEASE`).
* `-v`: Specifies the exact FreeBSD version to download from official servers.

### 2. Create your Main Ports Tree

Poudriere also needs the official FreeBSD ports tree to resolve base dependencies:

```bash
poudriere ports -c -p default
```

---

## How to Use with Poudriere

Follow these steps to register this overlay and build packages using Poudriere.

### 1. Clone the Repository

Clone this repository to a local directory on your FreeBSD system:

```bash
git clone https://github.com/xgui4/freebsd-ports.git /usr/local/xgui4-freebsd-ports
```

### 2. Register the Overlay in Poudriere

Register this directory as a local ports tree inside Poudriere:

```bash
poudriere ports -c -p xgui4-freebsd-ports -m null -M /usr/local/xgui4-freebsd-ports
```

### 3. Build a Port

To build a package from this overlay, use the `-O` flag to layer it on top of your main ports tree:

```bash
poudriere bulk -j <jail_name> -p <main_ports_tree> -O xgui4-freebsd-ports <category>/<port_name>
```

*(Replace `<jail_name>`, `<main_ports_tree>`, and `<category>/<port_name>` with your actual configuration environment).*
