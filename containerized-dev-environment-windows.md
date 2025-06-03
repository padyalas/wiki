# Containerized (Linux) Development Environment Setup in Windows

## WSL

- Enable the following windows features\
  ![alt text](images/wsl-windows-features.png)
- Restart when prompted
- Install Ubuntu app (generally the first search result for *ubuntu*) from Microsoft store\
  <ins>Note:</ins> Ubuntu default distribution for WSL can be installed using the command `wsl --install` from PowerShell (run as administrator). However, it was stuck at downloading Ubuntu in my case.
- When prompted, create default UNIX user account (e.g., ubunturoot) that can be used for *sudo* privileges
- If the launch window displays an error (e.g., Error code: Wsl/Service/CreateInstance/MountDisk/HCS/ERROR_FILE_NOT_FOUND)
- Run the following command in PowerShell to ensure WSL is running the default Ubuntu distribution
  - `wsl -l -v`
- Open Ubuntu app (terminal) and run the following commands
  - Check the Ubuntu version
    - `cat /etc/*release*`
  - Install updates
    - `sudo apt update && sudo apt upgrade`
  - Add wget (to retrieve content from web servers) and ca-certificates (to allow SSL-based applications to check for the authenticity of SSL connections)
    - `sudo apt install wget ca-certificates`
    - `sudo apt autoremove`

## Git for Windows

- Download and install *Git for Windows* with the following options (leave the rest with default options)\
  ![alt text](images/git-windows-1.png)
  ![alt text](images/git-windows-2.png)
  ![alt text](images/git-windows-3.png)

## Rancher Desktop

- Download and install *Rancher Desktop*
- Launch *Rancher Desktop* with the following options\
  ![alt text](images/rancher-desktop-1.jpg)
- Wait for the intialization to complete by checking the progress at the bottom right of the window. When finished, it should be empty as shown in red box below.\
  ![alt text](images/rancher-desktop-2.jpg)
- Set the *Preferences* for *Rancher Desktop* as below
  - Rancher Desktop &rarr; Preferences &rarr; Application &rarr; Behavior &rarr; Startup &rarr; Automatically start at login = Checked\
    Rancher Desktop &rarr; Preferences &rarr; Application &rarr; Behavior &rarr; Background &rarr; Start in the background = Checked\
    ![alt text](images/rancher-desktop-3.jpg)
  - Rancher Desktop &rarr; Preferences &rarr; WSL &rarr; Integrations &rarr; Ubuntu = Checked\
    ![alt text](images/rancher-desktop-4.jpg)

## Windows Terminal & Starship

- Install *Windows Terminal* from Microsoft Store
- Open *Windows Terminal* and set the default profile to *WSL Ubuntu*
  - Windows Terminal &rarr; Settings &rarr; Statup &rarr; Default profile = Ubuntu
- Run the following commands in *Windows Terminal (Ubuntu Profile)*
  - Ensure docker is running in WSL
    - `docker --version`
    - `docker ps`
  - Ensure git is installed
    - `git --version`
  - Set git config
    - `git config --global user.name "Your Name"`
    - `git config --global user.email "youremail@domain.com"`
    - `git config --global init.defaultBranch main`
  - Setup GCM for WSL
    - `git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/bin/git-credential-manager.exe"`
  - Install and configure *Starship* shell prompt
    - `curl -sS https://starship.rs/install.sh | sh`
    - Create the Starship configuration file:

        ```bash
        mkdir -p ~/.config

        cat << 'EOF' > ~/.config/starship.toml
        format = """$username@$hostname $directory$git_branch$git_status$character"""

        [username]
        show_always = true
        style = "yellow"
        disabled = false
        format = "[$username]($style)"

        [hostname]
        ssh_only = false
        style = "blue"
        disabled = false
        format = "[$hostname]($style)"

        [directory]
        truncation_length = 0
        truncate_to_repo = false
        symbol = "📁 "
        style = "cyan"
        format = "[$symbol$path]($style)"

        [git_branch]
        symbol = "🌱 "
        style = "purple"
        format = "[$symbol$branch]($style)"

        [git_status]
        symbol = "🔧 "
        style = "red"
        format = "[$symbol$all_status]($style)"

        [character]
        success_symbol = " [➜](green)"
        error_symbol = " [✗](red)"
        EOF
        ```

    - `echo 'eval "$(starship init bash)"' >> ~/.bashrc`
    - `source ~/.bashrc`

## Visual Studio Code

- Download and install *Visual Studio Code* with the following options (leave the rest with default options)\
  ![alt text](images/visual-studio-code-1.jpg)
- Install *Remote Development Extension Pack*\
  ![alt text](images/visual-studio-code-extension-1.jpg)
