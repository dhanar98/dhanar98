---
title: "How to add Bootstrap Icons in Next.js"
seoTitle: "How to add Bootstrap Icons in Next.js"
seoDescription: "Create a Next.js App and configure bootstrap-icons 2 ways using simple commands:
1. Install Bootstrap Icons
2. Adding icon fonts stylesheet CDN link in Next"
datePublished: Thu Jul 22 2021 10:42:50 GMT+0000 (Coordinated Universal Time)
cuid: cktx8q8dh0i2225s11x55ee8w
slug: how-to-add-bootstrap-icons-in-next-js
canonical: https://dhanar98.medium.com/how-to-add-bootstrap-icons-in-next-js-c691a21e7e4c
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706506258488/6e8c8724-5b97-49e2-ae99-94dfcc7bc2b6.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1706506272405/4f5d6af6-bc1b-4141-86af-244846ec7330.png
tags: bootstrap, github, bootstrap-4, reactjs, nextjs

---

## Create next-js app:

First, we need to create a [Next.js](https://nextjs.org/) application using npx or yarn according to your choice.

if you already create a Next.js app, then skip this part

Type this command in your terminal or cmd:

```bash
npx create-next-app project-name

(or)

yarn create-next-app project-name
```

In my case, I create the next app using npx like this

```bash
npx create-next-app bootstrap-icon-with-nextjs
```

Finally, we create out Next.js App

![Next.js — The React Framework](https://cdn.hashnode.com/res/hashnode/image/upload/v1632419998874/wB0Yx116w.png align="left")

We add bootstrap-icons in Next.js in two methods :

![©bootstrap-icons](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420001104/pXXpQZlXR.png align="left")

*©bootstrap-icons*

1. Install [Bootstrap Icons](https://icons.getbootstrap.com/) - including SVGs and icon fonts with npm.
    
2. Adding icon fonts stylesheet *CDN* link in \*\*Next.js \*\*inside \*\* \*\*Tag
    

Now, We start with a first method Installing Bootstrap-Icons using npm command. (This is a highly recommended method)

> **Install Bootstrap Icons:**

```bash
npm i bootstrap-icons
```

After installation, we need to import a CSS file in the **Next.js** custom page \*\*pages/\_app.js \*\*file.

![Adding bootstrap icons in _app.js](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420003337/8Iy7jtu2O.png align="left")

*Adding bootstrap icons in \_app.js*

> **Important: The \_app.js** file render all pages in the websites load the bootstrap-icons CSS

![RESULT CODE](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420005221/CrQ0W6o_a.png align="left")

*RESULT CODE*

Now, We move on to the second method🚶‍♂️

> **Adding icon fonts stylesheet CDN link in Next.js inside &lt;Head&gt; Tag :**

```bash
## Bootstrap-Icon CDN Link ##
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.5.0/font/bootstrap-icons.css">

## Import the module in the file ##
import Head from "next/head"
```

![Bootstrap-icon CDN link added in Next.js inside Head Tag](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420007132/xKj4XFhcW.png align="left")

***Bootstrap-icon CDN link added in Next.js inside &lt;Head&gt; Tag***

> **The Result for both methods:**

## **Screenshot:**

*Result for My code*

![Result for My code](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420008709/GYwADm5bv.png align="left")

Finally, we install Bootstrap-Icons both methods.

I push all the code in the GitHub repository Repository Link\[with two branches for both methods\] for more details read the `README.md` file in my repo =&gt;

%[https://github.com/dhanar98/bootstrap-icon-with-nextjs] 

```bash
💡Protip:
 Run your Next.js App with diffrent port using this command
  npx next -p 4_DIGIT_NUMBER
  E.X : npx next -p 1998
```

If this article really saves your time like the post.

![Good vibes Only © Unsplash](https://cdn.hashnode.com/res/hashnode/image/upload/v1632420010280/0lmVv4mYh.jpeg align="left")

***Good vibes Only © Unsplash***

**Reference Link:** Bootstrap-Icons:

%[https://icons.getbootstrap.com/]