---
title: "CI/CD pipeline best practice"
date: 2022-11-30
---
I have worked for various finance and tech companies.
What's the best practice I have ever seen regarding CI/CD pipeline?

1. There should be seperate staging and a production environments. 
2. Staging should allow engineers to test code changes without worrying affecting live customers.
3. Opening and updating PR should trigger test pipelines automatically.
4. There should be a format and lint step in the pipeline.
5. All the test, format and lint pipelines should have equivalent to be run locally.  
6. After code review and PR merging into master, pipeline should release changes into 
staging automatically.