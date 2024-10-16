---
title: "Setting up Github Pags"
date: 2022-11-01
---

The official [documentation](https://docs.github.com``/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
is long-winded. The essential steps are:

1. Create a repository 

    The repository must be named `<user>.github.io` and `user` must be lowercased:
    ![example](/assets/create-repository-name-pages.png)

2. Activate Github Pages: 

    Navigate to the settings page of the repository on GitHub, find the Github "pages" section and 
    select the branch and directory using the select source dropdown. 
   You can follow a more detailed instruction [here](
   https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-from-a-branch).

3. Add posts:

   Add posts in `_posts` directory. Posts have to have "front matter" which looks like:
    ```markdown
    ---
    title: "Setting up Github Pages in 5 minutes"
    date: 2022-11-04
    ---
    ```
    If you add a page that has a date in the future, that page **won't build**.     


4. Add pictures:

    If you want to add pictures, save them in `/assets` under the root of the repo 
    and reference the picture like: 
    ```
     ![text_to_show](/assets/picture_to_show.png)
    ```
   Don't forget to also commit and push the picture to make it appearing on the actual page!

5. Troubleshooting:
If your github page fails deploy due to timeout, check the size of your artifact (should be less than 1GB)
and also check the status of github: https://www.githubstatus.com/

    Reference: https://github.com/community/community/discussions/35197

6. Add a comment section

    Refer to: https://webapps.stackexchange.com/questions/165528/how-to-add-comments-in-blog-posts-on-github-pages-websites