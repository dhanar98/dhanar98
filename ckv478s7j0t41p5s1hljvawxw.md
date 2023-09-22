---
title: "Working with GitHub Basic Commands in Visual Studio Code - PART-1"
seoTitle: "Working with Github Basic Commands in Visual Studio Code"
seoDescription: "Working with Github Basic Commands in Visual Studio Code. How to clone a Repository, Add File,Commit Message and Create a Local branch in visual studio code"
datePublished: Sat Oct 23 2021 19:30:07 GMT+0000 (Coordinated Universal Time)
cuid: ckv478s7j0t41p5s1hljvawxw
slug: working-with-github-basic-commands-in-visual-studio-code-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1635000429696/9CjTBu4RH.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1635017178407/sPfrbH6lr.jpeg
tags: github, opensource, git, vscode, vscode-extensions

---

In this article, we are going to see GitHub basic commands in Visual studio code. Before going to that first we need to know the answers to these questions

1. What is **Github**?
2. What is **Visual Studio Code**?

## What is **GitHub**?
<p>**GitHub** is a provider of Internet hosting for software development and version control using Git. It offers the distributed version control and source code management functionality of Git, plus its own features.</p>

## What is **Visual Studio Code**?
<p>
**Visual Studio Code** is a source code editor that can be used with a variety of programming languages, including Java, JavaScript, Go, Node.js, Python and C++. Visual Studio Code combines the simplicity of a code editor with what developers need for their core edit-build-debug cycle.</p>

Download From Here ⬇️[![Download_Visual_studio_code](https://img.shields.io/badge/vscode-download-007ACC?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)](https://code.visualstudio.com/download)

Before using the basic commands in VS-CODE we need to install these two extensions

**1. GitLens**

**GitLens is the best GitHub extension in visual studio code.**
<details><summary>GitLens</summary> GitLens simply helps you better understand code. Quickly glimpse into whom, why and when a line or code block was changed.
</details>  


[![GitLens](https://img.shields.io/badge/GitLens_EXTENSION-212121?style=for-the-badge&logo=GitExtensions&logoColor=white)](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

**2.  Gitgraph**

**Git Graph extension is track user's activity**

<details>
<summary>
Gitgraph
</summary>View a Git Graph of your repository and easily perform Git actions from the graph. Configurable to look the way you want!
</details>

 [![GitGraph](https://img.shields.io/badge/GitGraph_EXTENSION-fff121?style=for-the-badge&logo=GitExtensions&logoColor=red)](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)

GitLens and Gitgraph Preview



![Github Commands.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1635015839602/b-tOF_wA3.png)

![Git Graph VS Code Extension Preview](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420060445/O37F_iWsh.png)

<p>**This is PART-1 in this series**- In this article, I perform 5 basic commands using VSCode and give a command snippet below</p>

### Github basic commands using visual studio code

#### Cloning a Git repository in visual studio code:
The Easiest way to Cloning a Git repository in visual studio code


![git-clone.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635013027329/E6l2Ph_2J.gif)
> command

```bash
git clone repo_url

E.X: git clone https://github.com/dhanar98/github-commands-in-visualstudio-code.git

```

####  Add a single file using Github using visual studio code
Adding a file in the GitHub repository

![git_add_single_file.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635013128031/-KM_R7JV6.gif)
> command

```bash
git add file_name

E.X: git add index.html
```

####  Adding all files in GitHub using visual studio code

![git_add_all_files.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635013445535/qooJ9IhUX.gif)

Add all files at the same time for the commit.
> command

```bash
git add .
```
#### Commit the files in visual studio code:
commit all your changes in visual studio code without command only give commit message in the source control panel to move your files to **changes to staged changes**

![Commit-the-code.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635013832632/lHiVUehcT.gif)

> command

```bash
git commit -m "commit message"

E.X: git commit -m "initial commit"
```

#### Create a local branch in Visual studio code
The Easiest way to create a local branch click the current local branch name in the bottom left corner and click the option create a new branch to give the branch name.


![create-new-branch-in-vscode.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635016125058/2HdUufBTk.gif)
> command

```bash
git branch new_branch

E.X: git branch new-branch
```
These Basic 5 Github commands using VSCode definitely help everyone. I Hope!!!
In **PART-2** we see another 5 commands using VSCode.
**Follow and Support.**💜


![randalyn-hill-.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1635018910634/_A021BfwJ.jpeg)



