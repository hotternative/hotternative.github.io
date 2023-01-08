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