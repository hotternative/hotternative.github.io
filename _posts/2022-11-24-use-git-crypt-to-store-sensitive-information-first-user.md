---
title: "Set up git-crypt to store sensitive information (2)"
date: 2022-11-24
---

After the initial set-ups in [the previous post]({% post_url 2022-11-22-use-git-crypt-to-store-sensitive-information-intro %}),
say you have a few secret files in `.gitcrypt_demo_secrets/` that contain secrets you'd like to push to git.

## Register the files to be encrypted
First, register the files to be encrypted
in `.gitattributes`, e.g.:
```
.gitcrypt_demo_secrets/production_environment.secrets filter=git-crypt diff=git-crypt
.gitcrypt_demo_secrets/staging_environment.secrets filter=git-crypt diff=git-crypt
```
It's also possible to specify a file pattern, e.g.
```
*.secrets filter=git-crypt diff=git-crypt
```
## Generate a new gpg key pair 
The next step is to add our first user. Run 
```shell
gpg --default-new-key-algo rsa3072 --full-generate-key
```
Then select Option 1 and follow the steps to generate the key pair. 
An email address and a name are required to generate the key pair.

Check the key is saved by `gpg`:
```shell
gpg --list-keys  
```

Then add the key to git-crypt:
```shell
git-crypt add-gpg-user <key_file_name>
```
This will create a `.git-crypt` directory in the root of the repo.

Now it's OK to add secrets into the repo. After adding the secrets,
```shell
git crypt status
```
should tell you that the secrets are encrypted, e.g.
```shell
not encrypted: .gitattributes
    encrypted: .gitcrypt_demo_secrets/production_environment.secrets
    encrypted: .gitcrypt_demo_secrets/staging_environment.secrets
...
```
Only after you see the above message, it's safe to git push the secret files to a remote repo.
Say it's a public repo, a random internet visitor will 
only see encrypted version of the secrets.
Check this encrypted file out:
[sample encrypted secret file](https://github.com/hotternative/hotternative.github.io/blob/main/.gitcrypt_demo_secrets/staging_environment.secrets)

Reference: 

[1] https://dev.to/heroku/how-to-manage-your-secrets-with-git-crypt-56ih