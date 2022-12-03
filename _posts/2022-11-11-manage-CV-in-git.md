---
title: "Manage your CV in git"
date: 2022-11-11
---
As a software engineer, you would receive many emails and job descriptions from
recruiters. 
Say you are open to consider new oppotunities.
You have a current CV in `.tex` and you receive a stream of job descriptions, 
See [here]({% post_url 2022-11-05-build-pdf-in-latex %}) about how to build pdf in latex.


* You would like to tailor your CV a bit based on the job description.
* While creating a tailored CV, you sometimes 
find it is a good idea to have the tailored info back in the main CV. 

Here is my workflow:
1. Keep a single, main, updated CV in master branch
2. When you get a job description, 
branch out for individual applications (save job description in branch)
3. Build PDF in the branch.
4. Merge useful bits in the branch's `.tex` file back to master.
