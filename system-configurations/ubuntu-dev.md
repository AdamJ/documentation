# Basic configurations for developing on a Ubuntu-based machine

## VirtualBox Guest Additions
```bash
$ sudo apt install virtualbox-guest-utils virtualbox-guest-dkms virtualbox-guest-x11
$ sudo reboot
$ lsmod | grep guest
```

## General
`$ sudo apt install vim`

## Install Fira Code for development environment
`$ sudo apt install fonts-firecode`

## Development Configuration
### install git
`$ sudo apt install git`

### install Nodejs
```bash
$ curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
$ sudo apt install -y nodejs
```
#### verify nodejs installation
```bash
$ nodejs
$ node -v
$ npm -v
```

### install Ruby
`$ sudo apt-get install ruby-full build-essential zlib1g-dev`

#### add Ruby Gems to .bashrc
```bash
$ echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
$ echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
$ echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
$ source ~/.bashrc
```

### install Jekyll
```bash
$ gem install jekyll bundler
$ bundle update --bundler
```

### install Gulp CLI globally
`$ sudo npm install gulp-cli -g`

### install JSHint glibally
`$ sudo npm install -g jshint`

## Increase the number of watch files (if needed)
`$ echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p`
