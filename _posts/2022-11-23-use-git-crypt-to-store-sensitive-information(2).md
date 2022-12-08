---
title: "Set up git-crypt to store sensitive information for a large engineering team"
date: 2022-11-23
---

After the initial set-ups in [the previous post]({% post_url 2022-11-22-use-git-crypt-to-store-sensitive-information %}),
say you have a file `sample.secrets` that contains some secrets you'd like to push to git.

## Register the file to be encrypted
This is to be done by a power-user or admin of the repository.

First, register this file in `.gitattributes` by adding a line, e.g.:
```
.gitcrypt_demo_secrets/production_environment.secrets filter=git-crypt diff=git-crypt
.gitcrypt_demo_secrets/staging_environment.secrets filter=git-crypt diff=git-crypt

```
Note, it's possible to specify a file pattern, e.g.
```
*.secrets filter=git-crypt diff=git-crypt
```
## Generate a new gpg key pair 
Say we now want to add a new engineer who is supposed to able to see
this encrypted file. The new engineer needs to run 
```shell
gpg --default-new-key-algo rsa3072 --full-generate-key
```
Then select Option 1 and follow the steps to generate the key pair. 
An email address and a name are required to generate the key pair.

The new engineer needs to take a note of the key file name, which looks like
`A49C7704A9C63894C75937897A4548F83C86403D`

Once the key pair is generated, obtain the public key by 
```
gpg --export -a <email_aaddress_supplied_when_generating_the_key_pair>
```
The new engineer will need to share the public key and the file name to an authroised 
user or an admin of the repo.

## Add a new user

This needs to be done by an existing git-crypt user or an admin of the repo.
The admin shall create a new key file 
```shell
touch <key_file_name>.gpg
```
Save the public key into the file just created.

Import GPG public key:
```shell
gpg --import <key_file_name>.gpg
```
Check the key is imported OK by
```shell
gpg --list-keys  
```

Add the user:
```shell
git-crypt add-gpg-user <key_file_name>
```

Now it's OK to add secrets into the repo. After adding the secrets
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
After this, it's safe to git push the secret file to a remote repo. 
Say it's a public repo, without a key, it's not possible to see the secrets. for example
[sample encrypted secret file](https://github.com/hotternative/hotternative.github.io/blob/main/.gitcrypt_demo_secrets/staging_environment.secrets)

Reference: 

[1] https://dev.to/heroku/how-to-manage-your-secrets-with-git-crypt-56ih