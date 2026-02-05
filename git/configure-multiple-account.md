### Configure multiple git accounts in system

* Create first config

```
cat ~/.gitconfig-personal-one
[user]
    name = abhilashindulkar
    email = axxxxx@gmail.com
[core]
    # Optional: specific SSH command if using different SSH keys (see next section)
    # sshCommand = "ssh -i /c/local/keys/abhi"
```

* Create second config

```
cat ~/.gitconfig-personal-two
[user]
    name = starkonbullet
    email = aixxxx@gmail.com
[core]
    # Optional: specific SSH command if using different SSH keys (see next section)
    # sshCommand = "ssh -i /c/local/keys/starkonbullet"
```

* Create global config

```
cat ~/.gitconfig
[includeIf "gitdir/i:c:/local/personal-one/"]
    path = ~/.gitconfig-personal-one

[includeIf "gitdir/i:c:/local/personal-two/"]
    path = ~/.gitconfig-personal-two
```

* Create SSH Keys

```
ssh-keygen -t rsa -b 2048 -C abhilashindulkar
ssh-keygen -t rsa -b 2048 -C starkonbullet
```

* Create SSH process and Add the key to agent

```
eval "$(ssh-agent -s)"

ssh-add ~/.abhi for personal-one
ssh-add ~/.starkonbullet for -personal-two
```
