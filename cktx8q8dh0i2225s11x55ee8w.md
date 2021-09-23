## How to add Bootstrap Icons in Next.js


## Create next-js app:

First, we need to create a [**Next.js](https://nextjs.org/) **application using npx or yarn according to your choice.

if you already create a Next.js app, then skip this part

Type this command in your terminal or cmd:

```
**npx create-next-app project-name**

(or)

yarn create-next-app project-name
```


In my case, I create the next app using npx like this

```
**npx create-next-app bootstrap-icon-with-nextjs**
```


Finally, we create out Next.js App

![Next.js — The React Framework](https://cdn.hashnode.com/res/hashnode/image/upload/v1632419998874/wB0Yx116w.png)*Next.js — The React Framework*

We add bootstrap-icons in Next.js in two methods :

![©bootstrap-icons](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420001104/pXXpQZlXR.png)*©bootstrap-icons*

1. Install [**Bootstrap Icons](https://icons.getbootstrap.com/) - **including SVGs and icon fonts with npm.

1. Adding icon fonts stylesheet *CDN* link in **Next.js **inside **<Head> **Tag

Now, We start with a first method
Installing Bootstrap-Icons using npm command. (This is a highly recommended method)
> **Install Bootstrap Icons:**

```
**npm i bootstrap-icons**
```


After installation, we need to import a CSS file in the **Next.js** custom page **pages/_app.js **file.

![Adding bootstrap icons in _app.js](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420003337/8Iy7jtu2O.png)*Adding bootstrap icons in _app.js*
> **Important:
**The** _app.js** file render all pages in the websites load the bootstrap-icons CSS

![RESULT CODE](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420005221/CrQ0W6o_a.png)*RESULT CODE*

Now, We move on to the second method🚶‍♂️
> **Adding icon fonts stylesheet CDN link in Next.js inside &lt;Head&gt; Tag :**

```
**## Bootstrap-Icon CDN Link ##**
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.5.0/font/bootstrap-icons.css">

## Import the module in the file ##
import Head from "next/head"
```


![**Bootstrap-icon CDN link added in Next.js inside &lt;Head&gt; Tag**](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420007132/xKj4XFhcW.png)***Bootstrap-icon CDN link added in Next.js inside &lt;Head&gt; Tag***
> **The Result for both methods:**

## **Screenshot:**

![Result for My code](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420008709/GYwADm5bv.png)*Result for My code*

Finally, we install Bootstrap-Icons both methods.

I push all the code in the GitHub repository
Repository Link[with two branches for both methods]
for more details read the README.md file in my repo
[**GitHub - dhanar98/bootstrap-icon-with-next.js**
*Clone project to run this commands step-1: clone a project git clone…*github.com](https://github.com/dhanar98/bootstrap-icon-with-nextjs)

```
**💡Protip:
  **Run your Next.js App with diffrent port using this command**
  npx next -p 4_DIGIT_NUMBER
  E.X : npx next -p 1998**
```


If this story really save your time give a clap 👏🏻 for me

![**Good vibes Only © Unsplash**](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420010280/0lmVv4mYh.jpeg)***Good vibes Only © Unsplash***

**Reference Link:**
Bootstrap-Icons:
[**Bootstrap Icons**
*Bootstrap Icons are published to npm, but they can also be manually downloaded if needed. Include the icon…*icons.getbootstrap.com](https://icons.getbootstrap.com/)

### **Check out my other article:**
[**Top 20 VSCode (Visual Studio Code) Extensions for Developers**
*Visual Studio Code is the most popular IDE in Web development. One of the best features is VSCode Extensions. I list…*medium.com](https://medium.com/@dhanar98/top-most-vscode-visual-studio-code-extensions-for-developers-cb20b8f0808)