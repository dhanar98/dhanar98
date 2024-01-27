---
title: "WordPress Sitemap Error - Error on line 2 at column 6: XML declaration allowed [FIXED]"
seoTitle: "How To Fix WordPress Sitemap Error - XML declaration allowed -SOLUTION"
seoDescription: "Discover how to fix the 'Error on line 2 at column 6: XML declaration allowed' issue in your WordPress sitemap. Follow step-by-step instructions to resolve"
datePublished: Fri Sep 22 2023 15:48:55 GMT+0000 (Coordinated Universal Time)
cuid: clmus1dc7000509jw4ilyetow
slug: wordpress-sitemap-error-error-on-line-2-at-column-6-xml-declaration-allowed-fixed
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/-WPrNEM_6dg/upload/3f7bb6346cb36caac56cccbcfa82ddc1.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695370949292/1d39ee1d-9c83-47bd-a20c-101be0df69d9.png
tags: wordpress, php, seo, sitemap, wordpress-development-services

---

## How To Fix WordPress Sitemap Error - XML declaration allowed \[SOLUTION\]

Fixing WordPress sitemap XML errors can help ensure that search engines can properly crawl and index your website. XML sitemaps provide valuable information about your site's structure and content.

### \*\*Troubleshooting and Fixing WordPress Sitemap XML Errors Methods \*\*

The error **"error on line 2 at column 6: XML declaration allowed only at the start of the document"** in WordPress is usually caused by a plugin or theme function adding empty whitespace at the beginning of the sitemap. This error indicates that there is a whitespace before the XML sitemap's source code.

#### **Check for Conflicting Plugins**

Sometimes, other plugins can conflict with your SEO plugin's sitemap generation. Deactivate other plugins one by one to see if any of them are causing the issue.

#### **Use a Reliable SEO Plugin**

Most WordPress users rely on SEO plugins like Yoast SEO or All in One SEO Pack to generate sitemaps. Make sure you have a reliable SEO plugin installed and properly configured.

#### **Check for Syntax Errors in XML**

Open your XML sitemap in a web browser or text editor and check for any syntax errors. It should be well-formed XML. Fix any issues you find.

[![XML_CHECKER](https://img.shields.io/badge/XMLCHECKER-333DFE.svg?style=for-the-badge&logo=Linktree&logoColor=white align="left")](https://www.liquid-technologies.com/online-xml-validator)

#### **Check for Syntax Error in Activated Theme**

* Check your theme's functions.php file for blank lines outside of the **&lt;? and ?&gt;** bracketed sections and other theme files.
    
* Deactivate the current theme and activate a default theme to encounter the issue because of the theme.
    

#### Include the PHP Script to Solve the Issue

* Download or Copy the Below PHP Script and add the file Root Directory of your WordPress.
    
* Then open the `index.php` and add the line `include('sitemap-fix.php');` right after the `<?php` tag.
    
* Check the Sitemap link of your website.
    

%[https://gist.github.com/dhanar98/5fa73a20d79d9e86c4a6e600d7942d8d] 

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>NOTE:</strong></div>
</div>

***Whenever you update the WordPress core, new files are added to your system fresh. Therefore, it's advisable to create a backup of these files. In the event of encountering sitemap errors after the update, you can restore the backup and include it in the index.php file.***

I hope this article is helpful to all of you. follow and support 💜💜💜💰

<div data-node-type="callout">
<div data-node-type="callout-emoji">📱</div>
<div data-node-type="callout-text"><strong>Connect With Me:</strong></div>
</div>

<center>
[![Gmail](https://img.shields.io/badge/gmail-F44336?style=for-the-badge&amp;logo=gmail&amp;logoColor=white)](mailto:dhanasekarravi98@gmail.com)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&amp;logo=linkedin&amp;logoColor=white)](https://www.linkedin.com/in/dhanar98/)
[![Whatsapp](https://img.shields.io/badge/WhatsApp-25D366.svg?style=for-the-badge&amp;logo=WhatsApp&amp;logoColor=white)](https://wa.me/9025165942/?text=hi%20%2C%20ping%20you%20from%20via%20hashnode%20blog)
</center>