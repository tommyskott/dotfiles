# Dot files

These are my dot files.  
Mainly for my own references but you might find something useful.  
Cheers! ✌️

## macOS Setup Guide - for developers

This is the official Borgenfalk & Skott macOS setup guide, to help you set up your dev environment as fast as possible.

_Why does this document exist?_ This is for the times when get a new computer and don't want to remember all the tools and steps that are needed to get your environment like you want it. So instead of googling and trying to remember what and how to install, simply follow this "well structured" guide.

1. First things first, login to your Apple ID and iCloud account so your documents and data can start syncing.

1. Turn on FileVault in System Settings -> Privacy & Security, to encrypt the data on your disk.

1. Turn on the Firewall in System Settings -> Network -> Firewall.

1. Download and install [1Password](https://1password.com/) so your login credentials are easy to access for the rest of the guide.

1. Download and install [Google Chrome](https://www.google.com/chrome/) web browser and sign in to your profile.

1. Download Xcode from the macOS [App Store](https://apps.apple.com/se/app/xcode/id497799835), or from Apple's [website](https://developer.apple.com/xcode/). When it has completed, install the Xcode cli tools with `xcode-select --install`.

1. Login to your other accounts (e-mail, calendar, notes) in System Settings -> Internet Accounts so the data can start syncing.

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
git -v
# git version 2.39.3 (Apple Git-146)

# set a global username
git config --global user.name "your_username"

# get the global username
git config --global user.name

# set a global email
git config --global user.email "your_email"

# get the global email
git config --global user.email
```

## SSH

[Follow the guide](/.ssh/README.md) on how to setup SSH config and adding new SSH keys.

## Visual Studio Code

Download and install [VS Code](https://code.visualstudio.com/) and add the extensions you need, from the list below.  
Open them in VS Code Marketplace or check the "Recommended extensions" tab in VS Code.

- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Even Better TOML](https://marketplace.visualstudio.com/items?itemName=tamasfe.even-better-toml)
- [GitHub Actions](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-github-actions)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Mustache](https://marketplace.visualstudio.com/items?itemName=dawhite.mustache)
- [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

### Profile settings & key bindings

You can import/export different profiles in VS Code but it's kind of buggy on macOS and VS Code defaults back to the default profile every time you restart VS Code (bug?). So for that reason, we are replacing our default settings instead of importing a new profile, so we don't have switch profile all the time.

1. Open VS Code with your default profile active and open settings `cmd + ,`.
1. Search for the setting to show settings as json instead of ui: `"workbench.settings.editor": "json"`.
1. Open your settings again but this time it should open in json format.
1. Copy and paste the contents of [settings.json](/visual-studio-code/settings.json) to your settings.json in VS Code and save.
1. Open Settings -> Keyboard Shortcuts in VS Code and click the icon in the upper right to show keybindings as json format instead of ui.
1. Copy and paste the contents of [keybindings.json](/visual-studio-code/keybindings.json) to your keybindings.json in VS Code and save.

## Terminal

Download and install [iTerm2](https://iterm2.com/), for a more customizable terminal. Download and import a [color scheme](https://iterm2colorschemes.com/), I like the [Dracula](https://raw.githubusercontent.com/mbadolato/iTerm2-Color-Schemes/master/schemes/Dracula.itermcolors) color sheme.

To prevent weird locale warnings when connecting to a VPS or similar, make sure to turn off the setting to set the locale automatically in Settings -> Profiles (Default) -> Terminal -> "Environment: Set locale variables automatically".

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

- [CleanMyMac X](https://macpaw.com/cleanmymac)
- [DaisyDisk](https://daisydiskapp.com/)
- [Dropbox](https://www.dropbox.com/install)
- [ImageOptim](https://imageoptim.com/mac)
- [Little Snitch](https://obdev.at/products/littlesnitch/index.html)
- [Mozilla Firefox](https://www.mozilla.org/en-US/firefox/new/)
- [The Unarchiver](https://theunarchiver.com/)
- [Toggl Track](https://toggl.com/track/)
- [Trello](https://trello.com/)

### Misc

- [Aerial Apple TV Screensaver](https://github.com/JohnCoates/Aerial)
- [Logitech MX Keys App](https://www.logitech.com/sv-se/setup/mxsetup/logi-options.html)
