---
title: "CI/CD pipeline best practice"
date: 2022-11-30
---
I have worked for various finance and tech companies.
What's the best practice I have ever seen regarding CI/CD pipeline?

1. There should be separate staging and production environments. 
   * Staging should allow engineers to test code changes without worrying affecting live customers.
   * There can be multiple production enviornments
2. Opening and updating a PR should trigger test pipelines automatically.
3. There should be a format and lint step in the pipeline.
4. All the test, format and lint pipelines should have equivalent to be run locally.  
5. After code review and PR merging into master, pipeline should release changes into 
staging automatically.