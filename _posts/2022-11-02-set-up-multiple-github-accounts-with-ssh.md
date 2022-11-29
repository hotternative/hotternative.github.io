---
title: "Using multiple GitHub accounts with SSH"
date: 2022-11-02
---

I have two GitHub accounts, a personal one and a work one. 
I want to use both accounts on same computer without typing password everytime, 
when doing git push or pull.

I also want git to distinguish the two accounts automatically, i.e. when committng to my personal 
repo, I don't need to worry that the author is my work account.


## How to?
1. [Generate ssh key pairs for accounts](https://help.github.com/articles/generating-a-new-ssh-key/) 
2. and [add them to GitHub accounts](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).
3. Edit/Create ssh config file (`~/.ssh/config`):

   ```conf
    Host github-personal
      HostName ssh.github.com
      UseKeychain yes
      IdentitiesOnly yes
      IdentityFile ~/.ssh/personal_github_key
    
    Host github-work
      HostName ssh.github.com
      UseKeychain yes
      AddKeysToAgent yes
      IdentityFile ~/.ssh/work_github_key
   ```
   
4. [Add ssh private keys to your agent](https://help.github.com/articles/adding-a-new-ssh-key-to-the-ssh-agent/):

   ```shell
   $ ssh-add ~/.ssh/personal_github_key
   $ ssh-add ~/.ssh/work_github_key
   ```

5. Test your connection

   ```shell
   $ ssh -T git@github-work
   $ ssh -T git@github-personal
   ```

   With each command, you may see this kind of warning, type `yes`:

   ```
   The authenticity of host 'github.com (192.30.252.1)' can't be established.
   RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:
   Are you sure you want to continue connecting (yes/no)?
   ```

   If everything is OK, you will see these messages:

   ```
   Hi <work_username>! You've successfully authenticated, but GitHub does not provide shell access.
   ```
   
   ```
   Hi <personal_username>! You've successfully authenticated, but GitHub does not provide shell access.
   ```

6. Now you can clone your personal repository with the personal ssh setup, e.g.
   ```shell
   $ git clone git@github-personal:hotternative/hotternative.github.io.git /path/to/personal/project
   ```
7. Before start working on your personal project, make sure to configure git username and email to be 
the personal one, e.g.
    ```shell
   $ cd /path/to/personal/project 
   $ git config --local user.email "l001d@hotmail.com"
   $ git config --local user.name  "hotternative"
   ```
If this is forgotten, it's possible to commit inadvertently with work account and then 
will have to take the pain of rewritting git his``tory which is recommeneded against.

8. The username and email that are set up in the previous step 
can be found in `/path/to/personal/project/.git/config`.

    In the config file, update the remote origin to us`e github-personal 
    ```conf
    [remote "origin"]
        url = git@github-personal:hotternative/hotternative.github.io.git
   ```
Reference: https://gist.github.com/oanhnn/80a89405ab9``023894df7