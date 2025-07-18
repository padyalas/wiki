# Jekyll

## Install Jekyll

- Run the following commands as sudo
  - `sudo apt-get update -y && sudo apt-get upgrade -y`
  - `sudo apt-get install ruby-full build-essential zlib1-dev`
- Run the following commands as regular user (non-sudo)
  - `echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc`
  - `echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc`
  - `echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc`
  - `ruby -v`
  - `gem -v`
  - `gem install jekyll bundler`
  - `jekyll -v`
  - `bundler --version`
