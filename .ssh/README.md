# SSH

## SSH guides on Github

[Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

[Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

## Generate a new SSH key

```bash
# go to your ssh folder
cd ~/.ssh

# generate a new key
ssh-keygen -t ed25519 -C "your_email@example.com"
# > Generating public/private key pair.

# start the ssh-agent in the background
eval "$(ssh-agent -s)"
# > Agent pid 59566
```

## Config file

This file will automatically load keys into the `ssh-agent` and store passphrases in your keychain.
`UseKeychain yes` is for macOS and if you've set a password for your ssh key - if you're on a Linux VPS, leave this out.

You can also add details about different servers you want to be able to connect to.  
E.g. `ssh your_custom_short_name` will connect to that server using the credentials you've added to that `Host` in the config file, see below.

```bash
# open the config file in nano editor, if it doesn't exist - create it with: touch ~/.ssh/config
nano ~/.ssh/config

# paste the code below to your config file
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519 # default key

# my vps on amazon
Host your_custom_short_name
  Hostname your_server_ip
  User your_server_username
  IdentityFile ~/.ssh/id_rsa_legacy # optional: specific private key for this server
```

## Add your key to the SSH agent

**Important!** Leave out `--apple-use-keychain` if NO password was set OR if you're on a VPS.

```bash
# add key to the ssh agent
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

## File and folder permissions

```bash
# ssh folder (drwx------)
chmod 700 ~/.ssh

# config file (-rw-r--r--)
chmod 644 ~/.ssh/config

# public key (-rw-r--r--)
chmod 644 ~/.ssh/id_ed25519.pub

# private key (-rw-------)
chmod 600 ~/.ssh/id_ed25519
```

## Copy your ssh key to a remote host

```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub your_custom_short_name
```

## Copy your public key for Github and similar services

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

## Connect to a server via SSH

```bash
# using one of your short names
ssh your_custom_short_name

# default way
ssh user@ip_address
```

## Troubleshooting

https://help.github.com/en/articles/error-permission-denied-publickey
