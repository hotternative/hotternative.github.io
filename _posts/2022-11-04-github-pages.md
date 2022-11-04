---
title: "Setting up Github Pages in 5 minutes"
date: 2022-11-04
---

The official [documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
is long-winded. The essential steps are:

1. Create a repository 

    The repository must be named `<user>.github.io` and `user` must be lowercased:
    ![example](/assets/create-repository-name-pages.png)

2. Activate Github Pages: 

    Navigate to the settings page of the repository on GitHub, find the Github "pages" section and 
    select the branch and directory using the select source dropdown. Follow a more detailed instruction [here](
https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-from-a-branch).

3. Add posts:

   Add posts in `_posts` directory. Posts have to have "front matter" which looks like:
    ```markdown
    ---
    title: "Setting up Github Pages in 5 minutes"
    date: 2022-11-04
    ---
    ```

