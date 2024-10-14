---
title: "More Bash Commands "
date: 2023-01-08
---

```shell
    for str in "${supported_python_versions_decimal[@]}"; do
      echo "supported 1: $str" >&2
    done
```
https://www.freecodecamp.org/news/bash-array-how-to-declare-an-array-of-strings-in-a-bash-script/
```
See [my previous post]({% post_url 2023-01-01-pyenv %}) for how pyenv Works and how to use it.

Bonus: to set up an env var in Python:
```python
import os
os.environ["VAR_NAME"] = var_value
```
Note that var_value must be of string type.

Reference: https://linuxize.com/post/bash-concatenate-strings/