---
title: Some helpful GitHub notes
tags: ['github', 'git',]
---
### Use ssh keys

Essentially cribbed from [this stackoverflow
article](http://stackoverflow.com/a/24572857).
Also, the [github doc](https://help.github.com/articles/generating-ssh-keys/).

#### Use `ssh-keygen` to generate a key

```bash
ssh-keygen
cat ~/.ssh/id_rsa.pub
```

Paste the output into the [SSH keys](https://github.com/settings/ssh) 
settings page at github.

#### Update `origin`

```bash
git remote rm origin
gir remote add origin git@github.com:<github username>/<repo>.git
```

It is essential that you use the `git@` user for the ssh address.
Once that is done, push your updates.

```bash
git push -u origin master
```
