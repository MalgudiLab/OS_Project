# Project Documentation: Linux File Compression and Encryption

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [File Compression](#file-compression)
    - [Compress All Resumes](#compress-all-resumes)
    - [Extracting Compressed Files](#extracting-compressed-files)
4. [File Encryption](#file-encryption)
    - [Encrypting the Aadhar Card](#encrypting-the-aadhar-card)
    - [Decrypting Files](#decrypting-files)
5. [Process Management](#process-management)
6. [Space Consumption Analysis](#space-consumption-analysis)
7. [Hidden Files](#hidden-files)
8. [Installation of Apache Web Server and Homebrew](#installation-of-apache-web-server-and-homebrew)

---

## Introduction

This documentation outlines the process of compressing user resumes, encrypting sensitive files (such as Aadhar cards), managing system processes, and installing packages on a Linux system. The following steps will guide you through file compression using `tar` and `gzip`, file encryption using `gpg`, and basic system tasks like monitoring disk usage and process management.

---

## Prerequisites

Ensure you have the following tools installed on your Linux system:
- `tar`: For archiving and compressing files.
- `gzip`: For file compression.
- `gpg`: For encryption and decryption.
- `apache2`: For installing the Apache web server.
- `brew`: For installing Homebrew and related packages.

You can install any missing tools using your system's package manager (e.g., `apt`, `yum`, or `brew`).

---

## File Compression

### Compress All Resumes

To compress all users' resumes stored in a specific folder, you can use the `tar` command with `gzip` compression.

```
tar -czvf resumes.tar.gz /path/to/resumes
```

Extracting Compressed Files
To extract the contents of the .tar.gz file, use the following command:

```
tar -xzvf resumes.tar.gz
```

Extracting to a Specific Directory:
```
tar -xzvf resumes.tar.gz -C /path/to/destination
```

### File Encryption
Encrypting the Aadhar Card

You can encrypt sensitive files (e.g., Aadhar card PDFs) using GPG. To allow both the user and the HR department to decrypt the file, use the following command:
```
gpg -c /path/to/HR/aadhar_card.txt
```
To Decrypt:
```
gpg -d /path/to/HR/aadhar_card.txt
```


Process Management

To list all the processes running on your Linux system, use:
```
ps -aux
```
List Processes Using Java:
```
ps -aux | grep java
```
Kill a Specific Process

Find the process ID (PID) from the list and use the kill command to stop it:
```
kill <PID>
```

### Space Consumption Analysis

To check the disk space usage for a specific user and list the top 10 largest files:
```
du -h /home/username | sort -rh | head -n 10
```

To hide the any file change the file name by adding prefix ".": eg: example.txt to .example.txt

To list the hidden files: 
```
ls -a
```


### Installation of Apache Web Server and Homebrew


To install Apache web server on a Linux system, use:
```
sudo apt update
sudo apt install apache2
```
Start the Apache server:
```
sudo systemctl start apache2
```
### Install Homebrew
To install Homebrew on Linux, execute the following command:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Once Homebrew is installed, you can use brew to install various packages:
```
brew install <package_name>
```