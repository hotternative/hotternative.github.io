---
title: "CI/CD pipeline best practice"
date: 2022-11-30
---
I have worked for various finance and tech companies.
What's the best practice I have ever seen regarding CI/CD pipeline?

## Staging 
1. There should be separate staging and production environments. 
   * Staging should allow engineers to test code changes 
   without worrying affecting live customers.
2. Ideally staging should allow branches to be deployed into it. If this not possible,
after code review and PR merging into master, pipeline should release changes into 
staging automatically.

## Test
1. There should be a format and lint step in the pipeline.
2. All the test, format and lint pipelines should have equivalent to be run locally.  
3. Opening and updating a PR should trigger test pipelines automatically.
