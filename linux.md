# Linux Administration Documentation Tree

## Overview
- **What is Linux Administration?**
  - Managing and configuring Linux systems
  - Ensuring system stability and security
- **Key Concepts**
  - Filesystem Hierarchy
  - User and Group Management
  - System Services and Daemons
- **Getting Started**
  - Accessing the Linux System
  - Basic Commands
  - System Overview

## File System
- **Navigating the File System**
  - **`cd` and `ls` Commands**
    - Scenario: Navigate to a directory and list its contents
    - Sample Code:
      ```bash
      cd /var/log
      ls -l
      ```
- **File and Directory Operations**
  - **Creating Files and Directories**
    - Scenario: Create a new directory and file
    - Sample Code:
      ```bash
      mkdir my_directory
      touch my_file.txt
      ```
  - **Copying and Moving Files**
    - Scenario: Copy and move files between directories
    - Sample Code:
      ```bash
      cp my_file.txt /tmp/
      mv my_file.txt /tmp/
      ```
  - **Deleting Files and Directories**
    - Scenario: Remove a file and a directory
    - Sample Code:
      ```bash
      rm my_file.txt
      rm -r my_directory
      ```

## User and Group Management
- **Creating and Managing Users**
  - **Adding Users**
    - Scenario: Add a new user to the system
    - Sample Code:
      ```bash
      sudo useradd newuser
      sudo passwd newuser
      ```
  - **Modifying Users**
    - Scenario: Change user information or password
    - Sample Code:
      ```bash
      sudo usermod -aG sudo newuser
      sudo passwd newuser
      ```
  - **Deleting Users**
    - Scenario: Remove a user and their home directory
    - Sample Code:
      ```bash
      sudo userdel -r newuser
      ```
- **Managing Groups**
  - **Creating and Managing Groups**
    - Scenario: Create a new group and add users to it
    - Sample Code:
      ```bash
      sudo groupadd mygroup
      sudo usermod -aG mygroup newuser
      ```
  - **Deleting Groups**
    - Scenario: Remove a group
    - Sample Code:
      ```bash
      sudo groupdel mygroup
      ```

## Permissions and Ownership
- **Understanding File Permissions**
  - **Viewing Permissions**
    - Scenario: Check permissions of files and directories
    - Sample Code:
      ```bash
      ls -l /etc/passwd
      ```
  - **Changing Permissions**
    - Scenario: Modify file permissions
    - Sample Code:
      ```bash
      chmod 755 my_script.sh
      ```
  - **Changing Ownership**
    - Scenario: Change the owner and group of a file
    - Sample Code:
      ```bash
      chown user:group my_file.txt
      ```

## Package Management
- **Installing Packages**
  - **Using `apt` on Debian/Ubuntu**
    - Scenario: Install a new package
    - Sample Code:
      ```bash
      sudo apt update
      sudo apt install nginx
      ```
  - **Using `yum` on CentOS/RHEL**
    - Scenario: Install a new package
    - Sample Code:
      ```bash
      sudo yum install httpd
      ```
- **Updating Packages**
  - **Updating System Packages**
    - Scenario: Update all installed packages
    - Sample Code:
      ```bash
      sudo apt upgrade
      sudo yum update
      ```
- **Removing Packages**
  - **Uninstalling Packages**
    - Scenario: Remove an installed package
    - Sample Code:
      ```bash
      sudo apt remove nginx
      sudo yum remove httpd
      ```

## System Monitoring and Performance
- **Viewing System Resources**
  - **Using `top` and `htop`**
    - Scenario: Monitor system processes and resource usage
    - Sample Code:
      ```bash
      top
      htop
      ```
- **Checking Disk Usage**
  - **Using `df` and `du`**
    - Scenario: Check disk space usage
    - Sample Code:
      ```bash
      df -h
      du -sh /home/user
      ```
- **Viewing System Logs**
  - **Using `journalctl` and `dmesg`**
    - Scenario: View system logs and messages
    - Sample Code:
      ```bash
      journalctl -xe
      dmesg | less
      ```

## Networking
- **Configuring Network Interfaces**
  - **Using `ifconfig` and `ip`**
    - Scenario: View and configure network interfaces
    - Sample Code:
      ```bash
      ifconfig
      ip addr show
      ```
- **Managing Firewall Rules**
  - **Using `ufw` and `iptables`**
    - Scenario: Configure firewall rules to allow or deny traffic
    - Sample Code:
      ```bash
      sudo ufw allow ssh
      sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
      ```
- **Testing Network Connectivity**
  - **Using `ping` and `netstat`**
    - Scenario: Test network connectivity and view open ports
    - Sample Code:
      ```bash
      ping google.com
      netstat -tuln
      ```

## System Services and Daemons
- **Managing Services**
  - **Using `systemctl`**
    - Scenario: Start, stop, and check the status of services
    - Sample Code:
      ```bash
      sudo systemctl start nginx
      sudo systemctl stop nginx
      sudo systemctl status nginx
      ```
- **Enabling and Disabling Services**
  - **Configuring Services to Start at Boot**
    - Scenario: Enable or disable services on boot
    - Sample Code:
      ```bash
      sudo systemctl enable nginx
      sudo systemctl disable nginx
      ```

## Backup and Recovery
- **Creating Backups**
  - **Using `rsync`**
    - Scenario: Backup files to a remote server
    - Sample Code:
      ```bash
      rsync -avz /home/user remote-server:/backup/
      ```
- **Restoring Backups**
  - **Restoring Files from Backup**
    - Scenario: Restore files from a backup directory
    - Sample Code:
      ```bash
      rsync -avz remote-server:/backup/ /home/user/
      ```

## Security
- **Managing Users and Permissions**
  - **Using `sudo` and `su`**
    - Scenario: Switch users and execute commands with elevated privileges
    - Sample Code:
      ```bash
      sudo su - user
      sudo command
      ```
- **Setting Up SSH Keys**
  - **Generating and Using SSH Keys**
    - Scenario: Configure SSH keys for secure access
    - Sample Code:
      ```bash
      ssh-keygen -t rsa -b 4096
      ssh-copy-id user@remote-server
      ```

## System Maintenance
- **Updating the System**
  - **Using Package Managers**
    - Scenario: Regularly update the system to ensure security
    - Sample Code:
      ```bash
      sudo apt update && sudo apt upgrade
      sudo yum update
      ```
- **Cleaning Up**
  - **Removing Unnecessary Files**
    - Scenario: Free up disk space by removing temporary files
    - Sample Code:
      ```bash
      sudo apt autoremove
      sudo yum clean all
      ```

