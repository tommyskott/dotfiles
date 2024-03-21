# Setup guide for macOS

This is the official B&S work station setup guide for macOS, to help you set up your dev environment as fast as possible.

_Why does this document exist?_ This is for the times when get a new computer and don't want to remember all the tools and steps that are needed to get your environment like you want it. So instead of googling and trying to remember what and how to install, simply follow this well structured guide.

1. First things first, login to your Apple ID and iCloud account so your documents and data can start syncing.

1. Turn on FileVault in System Settings -> Privacy & Security, to encrypt the data on your disk.

1. Turn on the Firewall in System Settings -> Network -> Firewall.

1. Download and install [1Password](https://1password.com/) so your login credentials are easy to access for the rest of the guide.

1. Download [Xcode](https://apps.apple.com/se/app/xcode/id497799835) from the macOS App Store, when it has completed, install the Xcode cli tools with `xcode-select --install`.

## OhMyZsh

Install the cli tool [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh) to boost your terminal with nice auto-completions, themes and much more.

## Homebrew

Install [Homebrew](https://brew.sh/), the missing package manager for macOS.

### Homebrew - Casks of Fonts

When Homebrew is installed, `tap` the [Casks of Fonts](https://github.com/Homebrew/homebrew-cask-fonts) and install the fonts you need.

```bash
# You only need to do this once!
brew tap homebrew/cask-fonts

# install the fonts
brew install font-inconsolata
brew install font-fira-code
brew install font-hack-nerd-font

```

## Php

Install the latest or a specific version of Php.

```bash
# latest version
brew install php

# a specific version
brew install php@8.2

# Load the version of php you need in ~/.zshrc
export PATH="/opt/homebrew/opt/php@8.2/bin:$PATH"
export PATH="/opt/homebrew/opt/php@8.2/sbin:$PATH"
```

## MariaDB

Install MySQL database distribution MariaDB.

```bash
brew install mariadb

# login with sudo/root - use your computer password!
sudo mysql -u root -p

# create new user
CREATE USER 'dev'@'localhost' IDENTIFIED BY 'dev';

# give privileges to new user "dev"
GRANT ALL PRIVILEGES ON * . * TO 'dev'@'localhost';
# Query OK, 0 rows affected (0.027 sec)

# flush all privileges
FLUSH PRIVILEGES;
# Query OK, 0 rows affected (0.001 sec)

# logout
exit

# restart mariadb
brew services restart mariadb
# Stopping `mariadb`... (might take a while)
# ==> Successfully stopped `mariadb` (label: homebrew.mxcl.mariadb)
# ==> Successfully started `mariadb` (label: homebrew.mxcl.mariadb)
```

## Node Version Manager

Install NVM so you can have multiple versions of Node installed at once and switch between them easily.

```bash
# this should've been printed to your ~/.zshrc
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

## Composer

Download and install [Composer](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-macos), the package manager for php. Follow the global install guide in their docs.

```bash
# for global package installations like e.g. Laravel Valet, make sure the vendor directory is in your "PATH", by adding this to your ~/.zshrc:
export PATH="$PATH:$HOME/.composer/vendor/bin"
```

## Laravel Valet

Install [Laravel Valet](https://laravel.com/docs/11.x/valet).  
When Valet is installed, setup your project like below.

```bash
# go to the web root of your project
cd ~/bucket/my-project/bedrock/web

# create symlinks
valet link borgenfalkskott-se
valet link borgenfalkskott-com

# create TLS certs
valet secure borgenfalkskott-se
valet secure borgenfalkskott-com

# list all valet sites
valet links
```

## Setup git

Create ssh keys and add them to github and other places.

```bash
# more info coming soon...
```

## Additional software

1. [Sequel Ace](https://apps.apple.com/se/app/sequel-ace/id1518036000)
1. Git Tower
1. VS Code
1. Sublime Text
1. Spotify
1. Discord
1. Slack
1. Affinity Photo / Designer / Publisher
