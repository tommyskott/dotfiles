# macOS Setup Guide - for developers

This is the official Borgenfalk & Skott work station setup guide for macOS, to help you set up your dev environment as fast as possible.

_Why does this document exist?_ This is for the times when get a new computer and don't want to remember all the tools and steps that are needed to get your environment like you want it. So instead of googling and trying to remember what and how to install, simply follow this "well structured" guide.

1. First things first, login to your Apple ID and iCloud account so your documents and data can start syncing.

1. Turn on FileVault in System Settings -> Privacy & Security, to encrypt the data on your disk.

1. Turn on the Firewall in System Settings -> Network -> Firewall.

1. Download and install [1Password](https://1password.com/) so your login credentials are easy to access for the rest of the guide.

1. Download Xcode from the macOS [App Store](https://apps.apple.com/se/app/xcode/id497799835), or from Apple's [website](https://developer.apple.com/xcode/). When it has completed, install the Xcode cli tools with `xcode-select --install`.

## OhMyZsh

Install the cli tool [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh) to boost your terminal with nice auto-completions, themes, plugins and much more. Follow the "Basic Installation" in their docs. Either go with the default theme or select one from the wiki [Themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes).

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

# don't forget to flush
FLUSH PRIVILEGES;

# logout
exit

# restart mariadb
brew services restart mariadb
# Stopping `mariadb`... (might take a while)
# ==> Successfully stopped `mariadb` (label: homebrew.mxcl.mariadb)
# ==> Successfully started `mariadb` (label: homebrew.mxcl.mariadb)

# list all brew services
brew services list
```

## Composer

Download and install [Composer](https://getcomposer.org/download/), the package manager for php.  
After the installation completes, follow the steps for a global install.

## Laravel Valet

Make sure the Composer vendor dir is in your "PATH".

```bash
# add vendor dir to your PATH in: ~/.zshrc
export PATH="$PATH:$HOME/.composer/vendor/bin"
```

Install [Laravel Valet](https://laravel.com/docs/11.x/valet).  
When Valet is installed, setup your local projects like below.

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

## Node Version Manager

Install [NVM](https://github.com/nvm-sh/nvm) so you can have multiple versions of Node/Npm installed at once and switch between them easily. **Important!** Don't install Node via Homebrew or the official installer, use NVM instead.

```bash
# After the installation completes, this should've been printed to your ~/.zshrc
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

## Git

Setup your global git settings so your commits are assigned to your user.  
Git comes pre-installed with macOS.

```bash
# set a global username
git config --global user.name "your_username"

# get the global username
git config --global user.name

# set a global email
git config --global user.email "your_email"

# get the global email
git config --global user.email
```

## VS Code

Download and install [VS Code]() and add your settings and key bindings to your default workspace profile.

## Additional software

A list of links to some of the tools I use or have used before.

### Communication

- [Discord](https://discord.com/)
- [Keybase](https://keybase.io/)
- [Slack](https://slack.com/)

### Creative

- [Affinity Designer](https://affinity.serif.com/en-us/designer/)
- [Affinity Photo](https://affinity.serif.com/en-us/photo/)
- [Affinity Publisher](https://affinity.serif.com/en-us/publisher/)
- [ColorSnapper 2](https://colorsnapper.com/)
- [DaVinci Resolve](https://www.blackmagicdesign.com/products/davinciresolve/)
- [Figma](https://www.figma.com/)

### Database

- [Postgres.app](https://postgresapp.com/)
- [Robo 3T](https://robomongo.org/)
- [Sequel Ace](https://sequel-ace.com/)

### Development

- [Crontab Guru](https://crontab.guru/)
- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
- [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)
- [Git Tower](https://www.git-tower.com/mac)
- [Google PageSpeed Insights](https://pagespeed.web.dev/)
- [Insomnia](https://insomnia.rest/)
- [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/)
- [Npm Semver Calculator](https://semver.npmjs.com/)
- [Paw](https://paw.cloud/)
- [Packagist](https://packagist.org/packages/borgenfalkskott/)
- [Sublime Text](https://www.sublimetext.com/)
- [SVG 2 JSX](https://svg2jsx.com/)
- [SVGOMG](https://jakearchibald.github.io/svgomg/)
- [TinyPNG](https://tinypng.com/)
- [Transmit](https://panic.com/transmit/)
- [VS Code](https://code.visualstudio.com/)
- [W3C CSS Validator](https://jigsaw.w3.org/css-validator/)
- [W3C Markup Validator](https://validator.w3.org/)
- [WordPress Packagist](https://wpackagist.org/)

### Entertainment

- [Battle.net](https://www.blizzard.com/en-us/download/confirmation?product=bnetdesk)
- [Spotify](https://www.spotify.com/se/)
- [Steam](https://store.steampowered.com/about/)

### Productivity

- [1Password](https://1password.com/)
- [CleanMyMac X](https://macpaw.com/cleanmymac)
- [DaisyDisk](https://daisydiskapp.com/)
- [Dropbox](https://www.dropbox.com/install)
- [ImageOptim](https://imageoptim.com/mac)
- [Little Snitch](https://obdev.at/products/littlesnitch/index.html)
- [Magnet](https://magnet.crowdcafe.com/)
- [Mozilla Firefox](https://www.mozilla.org/en-US/firefox/new/)
- [The Unarchiver](https://theunarchiver.com/)
- [Toggl Track](https://toggl.com/track/)
- [Trello](https://trello.com/)

### Terminal

- [iTerm2](https://iterm2.com/)
- [iTerm2 Color Schemes](https://iterm2colorschemes.com/)
- [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh)
- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
- [Powerline Fonts](https://github.com/powerline/fonts)

### Misc

- [Aerial Apple TV Screensaver](https://github.com/JohnCoates/Aerial)
- [Logitech MX Keys App](https://www.logitech.com/sv-se/setup/mxsetup/logi-options.html)
