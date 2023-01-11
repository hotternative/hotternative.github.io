---
title: "Bash Commands Related to Environment Variables"
date: 2023-01-08
---

```shell
env
```
will list all environment variables in the current shell session. Pipe it to `grep` to filter for interested ones.

```shell
export <key>=<value>
```
will add a new environment variable in the current shell session.

```shell
unset <key>
```
will remove an existing environment variable in the current shell session.

```shell
echo $<key>
```
will print the value of a specific key.

Finally, env vars can be used as parts of other command.
Say you have a pyenv environment 3.9.12, and you want to create a new pyenv virtual environment with it, 
the following will do:
```shell
export PYTHON_VERSION=3.9.12
pyenv virtualenv PYTHON_VERSION "py-${PYTHON_VERSION}" 
```
See [my previous post]({% post_url 2023-01-01-pyenv %}) for how pyenv Works and how to use it.

Bonus: to set up an env var in Python:
```python
import os
os.environ["VAR_NAME"] = var_value
```
Note that var_value must be of string type.

Reference: https://linuxize.com/post/bash-concatenate-strings/