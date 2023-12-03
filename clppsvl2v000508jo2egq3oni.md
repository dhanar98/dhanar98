---
title: "Master Laravel String Functions for Seamless Blog Application Development"
seoDescription: "This insightful blog post delves into the mastery of Laravel string functions, empowering you to streamline your blog development process."
datePublished: Sun Dec 03 2023 18:12:41 GMT+0000 (Coordinated Universal Time)
cuid: clppsvl2v000508jo2egq3oni
slug: master-laravel-string-functions-for-seamless-blog-application-development
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699504369077/58c14398-6872-48b6-81f6-cd59693e96ce.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699508972096/ec2da9be-3312-4388-8144-dcf6748f775d.png
tags: blogging, laravel, php, laravelframework, laravel-10

---

## Harness the Power of Laravel String Functions for Effortless Blog Development

Laravel string functions are a powerful tool that can be used to make your blog application development more efficient and effective. In this blog post, we will discuss some of the most useful Laravel string functions and how to use them to improve your blog application.

## Laravel String Functions Must Know for Blog Development

**Hello, Web Artisans**, When It comes to blog development a set of elements  
we need to take a look at URLs, Heading Tags and Other Elements With Different Letter Cases. For Blog Development A Set of Laravel functions helps to reduce our work and a more flexible way to handle those operations easily. Let's move on to the topic now ...

### Covert a string to slug or Create a string to URL format.

**Str::slug():** This function is used to generate a URL-friendly "slug" from a given string. It's commonly used for creating clean and SEO-friendly URLs.

```php
<?php
use Illuminate\Support\Str;

$articleTitle = 'Master Laravel String Functions for Seamless Blog Application Development';

echo Str::slug($articleTitle);
# Output : master-laravel-string-functions-for-seamless-blog-application-development
```

**Str::kebab():** This function is used to generate a slug format but some exceptional characters in the words are not converted to URL separator.

```php
<?php
use Illuminate\Support\Str;

$dictionaryExTitle = 'Create a React.js Application in Windows';

echo Str::kebab($dictionaryExTitle);
# Output : create-a-react.js-application-in-windows

echo Str::slug($dictionaryExTitle,'-','en',['.' => '-']);
# Output : create-a-react-js-application-in-windows
```

✅️The Best Option is **Str::slug()**

**This function accepts 4 parameters:**

* **Title** - The String we need to convert to slug format.
    
* **Separator** - This helps to separate the words in a string (usually in blog development ( - hyphen) is used.
    
* **Language** - The Language Supported in Laravel Core.
    
* **Dictionary** - It Converts some special characters to words. (E.x: / =&gt; 'slash')
    

### Convert a string to Headline

**Str::headline() -** This function generates a title as each first letter is a capitalized word with proper spacing between the words.

> ✅ The `headline` method will convert strings delimited by casing, hyphens, or underscores into a space.

```php
<?php
use Illuminate\Support\Str;

$slug = 'master-laravel-string-functions-for-seamless-blog-application-development';

echo Str::headline($slug);
# Output : Master Laravel String Functions For Seamless Blog Application Development
```

### Display the Content Using Characters Count

**Str::limit() -** Display the content excerpt using this method to show the limited number of characters for the particular post (character-based limit).

```php
<?php
use Illuminate\Support\Str;

$contentExcerpt = 'Str::limit() -  Display the content excerpt 
using this method to show the limited number of characters for the particular post.';

echo Str::limit($contentExcerpt,50,'.....');
# Output : Str::limit() -  Display the content excerpt using....
```

**This function accepts 3 parameters:**

* **content -** The content for the post to limited.
    
* **limit -** The number of characters to be shown.
    
* **end -** The characters in the end with special characters.
    

### Display the Content Using Words Count

**Str::words() -** Display the content based on words based in the post excerpt.  
this function helps to show the article excerpt with a limited number of words and is also used for bigger titles.

```php
<?php
use Illuminate\Support\Str;

$contentExcerpt = 'Str::words() - Display the content based on words based in the post excerpt.
                   this function helps to show the article excerpt with a limited number of words 
                    and is also used for bigger titles.';

echo Str::words($contentExcerpt, 10, '-->');
# Output : Str::words() - Display the content based on words based in -->
```

This function accepts 3 parameters:

* **content** \- The content for the post to limited.
    
* **words** \- The number of words to be shown.
    
* **end** \- The characters in the end with special characters.
    

### Count the Words In the Post Content

**Str::wordCount -** This function helps to count the number of words in the post content.

```php
<?php
use Illuminate\Support\Str;

$numberOfWordsInContent = 'Str::wordCount - This function helps to count the number of words in the post content.';

echo Str::wordCount($numberOfWordsInContent);
# Output : 16
```

**This function accepts 2 parameters:**

* **content -** The content for the post to count the words
    
* **characters -** The characters need to be considered as words.
    

### Markdown-based Content Blog in Single Method

**Str::markdown() -** This method converts GitHub-flavored Markdown into HTML using [CommonMark](https://commonmark.thephpleague.com/) ✅

All kinds of markdown-based elements convert into single post content to HTML String to Display in Post.

```php
use Illuminate\Support\Str;
 
$html = Str::markdown('# Laravel');
 
# Output: <h1>Laravel</h1>
```

### Creating a Hashnode-Based Markdown Typed Blog Platform In Laravel For Developers Is Easy

#### Simple Steps to create the blog:

* Create a Database Design Schema For the Blog Post.
    
* Design the Content Writing Platform in Markdown Typed Based.
    
* Design the Home and Single Post to show the article.
    
* Store the markdown code string in the content in the post table.
    
* convert the string using this function **Str::markdown**
    
* Code Highlighting Blog feature Refer [Prism JS - Code Format Highlight](https://prismjs.com/)
    

### Helpers in Blog Development

If you are looking for Premium-based features in the application create some string Helper Functions to Customize.

#### **Excerpts based on words and characters**

```php
<?php
# Filename : app/helpers.php
use Illuminate\Support\Str;

if (!function_exists('wordsOrCharacter')) {
    function wordsOrCharacter(string $type = '', string $content = '', int $count = 15, string $end = '')
    {
        if ($type === 'word') {
            return Str::words($content, $count, $end);
        }

        if ($type === 'character') {
            return Str::limit($content, $count, $end);
        }
    }
}
```

* **Blade Template:** `{!! wordsOrCharacter($post->excerpt_type, $post->content, 18, '###') !!}`
    

---

#### **Reading Time For the Blog Post**

* ```php
    <?php
    # Filename : app/helpers.php
    use Illuminate\Support\Str;
    
    if (!function_exists('calculateReadingTime')) {
        function calculateReadingTime($content)
        {
            $word_count = Str::wordCount($content);
            $reading_time = ceil($word_count / 200);
    
            if ($reading_time == 1) {
                $timer = " minute";
            } else {
                $timer = " minutes";
            }
            $total_reading_time = $reading_time . $timer;
            return $total_reading_time;
        }
    }
    ```
    
* **Blade Template:** `{!! calculateReadingTime($post->content) !!}`
    

---

#### Convert a Post Date to Facebook Notification Timing Type Conversion - For Humans

```php
<?php

use Carbon\Carbon;

if (!function_exists('convertForHumans')) {

    function convertForHumans(string $date, string $dateFormat = 'Y-m-d') {
        $notificationTime = Carbon::createFromFormat($dateFormat, $date)->diffForHumans();
        return $notificationTime;
    }
}

$dateString = '2023-12-02';
echo convertForHumans($dateString);
```