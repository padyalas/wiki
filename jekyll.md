# Jekyll

## Install Jekyll

- Run the following commands as sudo
  - `sudo apt-get update -y && sudo apt-get upgrade -y`
  - `sudo apt-get install ruby-full build-essential zlib1g-dev`
- Run the following commands as regular user (non-sudo)
  - `echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc`
  - `echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc`
  - `echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc`
  - `source ~/.bashrc`
  - `ruby -v`
  - `gem -v`
  - `gem install jekyll bundler`
  - `jekyll -v`
  - `bundler --version`

## Create Jekyll Site

- GitHub
  - Create a repository with default options (Public and no README file)
- Local Environment
  - `jekyll new [site]`
  - Update the following in _config.yml file
    - `baseurl: [github-repo]`
  - `git init`
  - `git checkout -b gh-pages`
  - `git status`
  - `git add .`
  - `git commit -m "initial commit"`
  - `git remote add origin https://github.com/[github-user]/[github-repo].git`
  - `git push origin gh-pages`
- GitHub
  - Go to [github-repo] > Settings > Pages > Visit site