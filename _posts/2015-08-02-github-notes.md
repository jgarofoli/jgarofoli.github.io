---
title: Some helpful GitHub notes
originaldate: 2015-08-02
tags: ['github', 'git',]
---
Similar to my [vim]({% post_url 2015-07-26-vim-notes %}) 
[notes]({% post_url 2015-08-01-vim-commands %}), 
I'll update this article over time.

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
