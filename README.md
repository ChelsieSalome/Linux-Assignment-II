# System Setup and User Creation Scripts
# Assignment 2
# SALOME CHELSIE LELE WAMBO - A01372274

This script is designed to simplify system setup by creating symbolic links for configuration files and installing essential packages. It’s useful for setting up multiple configuration files across directories (like bin and config) and automating package installations. The script includes options for creating symbolic links, installing packages, or performing both tasks simultaneously.

This repository contains a set of bash scripts designed for system setup and user creation on a Linux-based system. The scripts are organized into two directories: `system_setup` and `user_creation`.

## Directory Structure

- `system_setup/`:
  - `packages_list`: A text file listing the packages to be installed.
  - `installation`: A bash script to install the packages listed in `packages_list`.
  - `symlinks`: A bash script to create symbolic links for configuration files.
  - `system_setup`: A script that automates the overall system setup process by calling the `installation` and `symlinks` scripts.
  
- `user_creation/`:
  - `user_script`: A bash script for creating a new user on the system, including setting up home directories, groups, and shells.

## Scripts Overview

### `system_setup/`

1. **`packages_list`**  
   This file contains a list of packages that are to be installed on the system. Each line should represent a single package name.

2. **`installation`**  
   A bash script that reads from the `packages_list` file and installs the listed packages using a package manager (`pacman`). It automates the installation process by looping through the list of packages and ensuring they are installed.

   #### Usage:
   `./installation`

3. **`symlinks`**
    A bash script that creates symbolic links for configuration files.Those files are cloned from a remote repository using git. These links allow to store and access configuration files in a central location without needing to manually copy them into each user's directory.

    #### Usage:

    ./symlinks
    ./system_setup
    This script automates the entire system setup process by executing both the installation and symlinks scripts. It's a one-stop script for setting up the system by installing packages and creating the necessary symbolic links.
    This script should be run with sufficient privileges (e.g., using sudo), as it installs packages and modifies system configurations.

4. **`user_creation/`**

    #### Usage
    **`user_script`**
    A bash script that automates the process of creating a new user on the system. This script will:

    * Check if the user already exists.
    * Create a home directory.
    * Set up the default shell.
    * Add the user to any specified groups.
    * Copy default files from /etc/skel to the new user's home directory.
#### Usage:
    To create a new user, run the following command:


    ./user_script -u <username> -s <shell> -g <groups>
    -u <username>: The username of the new user.
    -s <shell>: The shell for the new user (e.g., /bin/bash). Defaults to /bin/bash if not provided.
    -g <groups>: A comma-separated list of groups to add the user to (optional).
    

### Prerequisites for Running the Scripts
* Bash (or a compatible shell) is required to run these scripts.
* The user_script in the user_creation folder requires root privileges for creating users, setting passwords, and adding to groups.
* Ensure you have sufficient disk space and system resources when running system_setup, especially if many packages are being installed.
* The scripts assume the system is based on a Linux environment.

### Usage Instructions

* Ensure the scripts: **symlinks**, **installation** & **system_setup** are in the same directory.
* Make the scripts executable:


`chmod +x system_setup/*.sh user_creation/user_script`

* Run the scripts:

* To set up the system:

    ./system_setup/system_setup

* To create a user:

    ./user_creation/user_script -u <username> -s <shell> -g <groups>


