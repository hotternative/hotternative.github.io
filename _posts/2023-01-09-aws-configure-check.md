---
title: "AWS configuration check"
date: 2023-01-09
---

If you have multiple ways (like with env vars/profile/etc) to log into AWS CLI, sometimes it's confusing why log-ins are not working. 
```shell
aws configure list
```
is what I find very useful in figuring out current configuration.

You'll find
```shell
aws configure list
      Name                    Value             Type    Location
      ----                    -----             ----    --------
   profile                <not set>             None    None
access_key                <not set>             None    None
secret_key                <not set>             None    None
    region                <not set>             None    None
```
if nothing is set up.

Or 
```shell
                 
      Name                    Value             Type    Location
      ----                    -----             ----    --------
   profile      production-engineer              env    ['AWS_PROFILE', 'AWS_DEFAULT_PROFILE']
access_key     ****************55FP      assume-role    
secret_key     ****************EuB7      assume-role    
    region                eu-west-1      config-file    ~/.aws/config

```
if you have something set up correctly. 

Also try `aws s3 ls` which is usually very fast.
