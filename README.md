# Puppet LAMP Stack & User Configuration

## Overview

This repository contains two Puppet manifests:

- `lamp_stack_server.pp`
- `server_users_groups.pp`

Both of these files are simple Puppet manifests that are configuration as code, defining parts of our infrastructure for a simple web server hosted on Ubuntu.

---

## lamp_stack_server.pp

This Puppet manifest enumerates the various packages and services necessary for this web server. Also contains checks to ensure the installations are in place before proceeding.

### To Run

You must have `sudo` permissions to execute this manifest.

1. Navigate to the directory containing the file
2. Run the following command:

```bash
sudo puppet apply lamp_stack_server.pp
```

---

## server_users_groups.pp

This file contains a set of premade users and groups to be added to the system. This file adds user0X, ranging from 4 to 7. The file can be changed to add any variety of users as long as the format of the file remains the same. If you choose to customize your users, you MUST use the command

```bash
openssl passwd -6 -salt xyz <thepasswordyouwanttohash>
```
to get the hash of the password for the user you are making, and enter this hash as the user's password in the puppet manifest.

### To Run

Once necessary changes are made for your system, use the command 

```bash
sudo puppet apply server_users_groups.pp
```
to create the users. After that, you may verify the successful creation of the users and groups with
```bash 
cat /etc/passwd
```
and
```bash
cat /etc/group
```
to check the users and the groups respectively.
