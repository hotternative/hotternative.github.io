---
title: "Build pdf file with Latex in Mac"
date: 2022-11-12
---

1. First, uninstall the pre-installed version
    ```
    brew uninstall mactex
    ```
2. Download the latest version from [MacTex](https://tug.org/mactex/mactex-download.html)
3. Install the downloaded one by double-clicking the downloaded package and follow the instructions
4. After install, check pdflatex is available in `/Library/Tex/texbin` 
5. Add `pdflatex` to path
    ```
    export PATH="/Library/Tex/texbin:$PATH"
    ```
6. check it now can be found:
    ```
    which pdflatex
    ```
7. to use it, simply 
    ```
    pdflatex <foo.tex>
    ```

Reference: [tex.stackexchange.com](https://tex.stackexchange.com/questions/220/i-want-to-start-using-latex-on-mac-os-x-where-do-i-start?noredirect=1&lq=1)