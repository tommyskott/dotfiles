# SSH

## SSH guides on Github

[Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) 

[Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

## Generate a new SSH key

```
ssh-keygen -t rsa -b 4096 -C "you@domain.com"
> Generating public/private rsa key pair.
```

## Start the ssh-agent in the background

```
eval "$(ssh-agent -s)"
> Agent pid 59566
```

## Setup config file

This will automatically load keys into the ssh-agent and store passphrases in your keychain.
"UseKeychain yes" is for macOS, if you're on a VPS, leave this out.

```
sudo atom ~/.ssh/config

Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa

Host your_shortname
  Hostname <ip-address>
  User youruser
  IdentityFile ~/.ssh/id_rsa.pub
```

## Add your key to the SSH agent

This is for macOS, if you're on a VPS, run this command without -K, since that's for keychain.

```
ssh-add -K ~/.ssh/id_rsa
```

## And some permissions for the files

```
chmod 644 ~/.ssh/config
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
chmod 600 ~/.ssh/*.pem
```

## Copy your ssh key to a remote host

```
ssh-copy-id -i ~/.ssh/id_rsa.pub <remote-host>
```

## Copy your public key for Github and similar services

```
pbcopy < ~/.ssh/id_rsa.pub
```

## Connect to a server via SSH

```
ssh your_shortname
```

## Troubleshooting

https://help.github.com/en/articles/error-permission-denied-publickey
