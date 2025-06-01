# Linux (development) environment setup in Windows

## Windows Terminal
* Install *Windows Terminal* from Microsoft Store

## WSL
* Enable the following windows features
  * Virtual Machine Platform
  * Windows Subsystem for Linux
* Restart when prompted
* Install Ubuntu app (generally the first search result for *ubuntu*) from Microsoft store\
  <ins>Note:</ins> Ubuntu default distribution for WSL can be installed using the command `wsl --install` from PowerShell (run as administrator). However, it was stuck at downloading Ubuntu in my case.
* When prompted, create default UNIX user account (e.g., ubunturoot) that can be used for *sudo* privileges
* Run the following command in PowerShell to ensure WSL is running the default Ubuntu distribution
  * `wsl -l -v`
* Set the default profile of Windows Terminal to WSL Ubuntu
  * Windows Terminal &rarr; Settings &rarr; Statup &rarr; Default profile = Ubuntu
* Open Windows Terminal as administrator
  * Check the Ubuntu version
    * `cat /etc/*release*`
  * Install updates
    * `sudo apt update && sudo apt upgrade`
  * Add wget (to retrieve content from web servers) and ca-certificates (to allow SSL-based applications to check for the authenticity of SSL connections)
    * `sudo apt-get install wget ca-certificates`
    * `sudo apt autoremove`

## Git for Windows
* Download and install *Git for Windows* with the following options
* 

# Git Bash
* Setting MSYS_NO_PATHCONV to a non-empty value (e.g., 1 or true) disables automatic path conversion. This means that if you enter a Windows-style path, it won't be automatically converted to a Unix-style path. Instead, it will be treated as-is.
* Delete multiple git local branches: ``` git branch -d `git branch --list 'feature/*'` ```

# AWS
* List aws profiles: `aws configure list-profiles`
* View a specific aws profile: `aws configure list --profile [profile name]`
* Update region for an aws profile: `aws configure set region [region code] --profile [profile name]`
* Get current account: `aws sts get-caller-identity`

# Terraform
* Remove lock on terraform state: `terraform force-unlock -force <ID>`
