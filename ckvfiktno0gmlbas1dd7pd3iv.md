---
title: "Working with GitHub Basic Commands in Visual Studio Code - PART-2"
seoTitle: "Working with GitHub Basic Commands Using Branches in VS CODE"
seoDescription: "Working with GitHub Basic Commands Using Branches in VS CODE - Push and Pull a branch, Git Stash and Apply, Delete a local branch"
datePublished: Sun Oct 31 2021 17:35:31 GMT+0000 (Coordinated Universal Time)
cuid: ckvfiktno0gmlbas1dd7pd3iv
slug: working-with-github-basic-commands-in-visual-studio-code-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1635681533782/YzSQhQ7Hw.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1635701192835/lw6cmUou3.jpeg
tags: github, web-development, vscode, developer-tools

---

## Github basic commands using visual studio code

Read the PART-1 click here⬇️
[![AutoRenameTag](https://img.shields.io/badge/Working_with_github_basic_commands_in_visual_studio_code_part_1-ffcc00?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)](https://dhanar98.hashnode.dev/working-with-github-basic-commands-in-visual-studio-code-part-1)

**GITHUB NEW UPDATE:**

%[https://twitter.com/github/status/1453832487067701252?s=20]

**This is PART-2 in this series**- In this article, I perform 5 basic commands using VSCode and give a command snippet below

## 1. Push a local branch in visual studio code

Pushing a local branch to GitHub in visual studio code is the easiest way to publish the changes button.
> "command"

```bash
      git push origin local_branch_name

     E.X: git push origin new_branch
``` 

![push_a_branch.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635683835934/0jb0CUAGo.gif)

## 2. Pull the latest code for the local branch in visual studio code

> "command"

```bash
      git pull

     E.X: git pull 
``` 


Pull the latest code for a current local branch click the bottom left corner refresh button.

![pull_the_code_origin.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635684462078/PH-ky6mPG.gif)

## 3. Delete the local branch in visual studio code
Delete local branch Press  <kbd>ctrl+shift+p</kbd> and select **Delete the branch**

> "command"

```bash
    git branch -d <local-branch>

    E.X: git branch -d new_branch
``` 


![delete_a_branch.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635686489783/85gDCS1eA.gif)


## 4. Stash a code in visual studio code

### **What is Stash?**
<p>You need some temporary space, where you can store your partial changes and later on commit them.</p>

<p>In Git, the stash operation takes your modified tracked files, stages changes, and saves them on a stack of unfinished changes that you can reapply at any time.</p>


> "command"

```bash
    git stash push -m <stash-message>

    E.X: git stash push -m "stash part-2"
``` 

Apply stash for recent changes Press  <kbd>ctrl+shift+p</kbd> and select ***Git:Stash***


![stash_in_vscode.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635699673208/Bmn3W7ukM.gif)

## 5. Stash apply in visual studio code

### **What is Stash Apply?**

<p>If you want to keep the changes in the stash as well, you can use git stash apply instead.</p>

Apply stash for recent changes Press  <kbd>ctrl+shift+p</kbd> and select ***Git:Apply Stash***

> "command"

```bash
    git stash apply <stash_id>

    E.X: git stash apply stash@{2}
``` 


![stash_apply_in_vscode.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1635700641915/K6atsU7yR.gif)

These Basic 5 Github commands used in VSCode definitely help everyone. I Hope!!! In PART-3 we see another 5 commands using VSCode. **Follow and Support.**💜


![motivational.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1635700900791/oRZC7TXUJ.jpeg)
