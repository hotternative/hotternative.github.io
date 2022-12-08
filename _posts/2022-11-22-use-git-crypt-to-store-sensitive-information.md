---
title: "Set up git-crypt to store sensitive information (1)"
date: 2022-11-22
---

It is well-known that you shouldn't store passwords, keys or other sensitive information
in your codebase.
However, with infrastructure as code, it would be very tempting to do the opposite.

I have seen people keeping a `.config` file outside the codebase and put it in manually at the time of deployment. 
This works for a small amount of deployments but doesn't scale well 
because of the manual steps involved, 
and the occasional needs to use a different set of secrets based on the type of deployments.
I have also seen people completely ignoring the rule and hard-coded sensitive information in codebase. 

`git-crypt` is a tool that allows sensitive information to be saved in git (so that instructure as code doesn't involve manual steps to put in sensitive information) but only
accessible by authorised personnel. It  takes a little time to set up, but is well worth the effort in the long run.

### Key feature of git-crypt
* Files which you choose to protect are encrypted when committed, and decrypted when checked out. 
* git-crypt lets you freely share a repository containing a mix of public and private content. developers without the secret key can still clone and commit to a repository with encrypted files.  
See more information in [git-crypt repo](https://github.com/AGWA/git-crypt)

### Install and Set-up
First, you need to install it by following 
[INSTALL.md](https://github.com/AGWA/git-crypt/blob/master/INSTALL.md)
For Mac OS, it's simply
```shell
brew install git-crypt
```

To set up a repository
```shell
git-crypt init
```

See [the next post]({% post_url 2022-11-23-use-git-crypt-to-store-sensitive-information(2) %}) for more information setting it up.
Reference: 

[1] https://dev.to/heroku/how-to-manage-your-secrets-with-git-crypt-56ih