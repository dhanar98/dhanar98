---
title: "How To Send Application Logs To Telegram In Laravel"
seoTitle: "2024 - How To Send Application Logs To Telegram In Laravel"
datePublished: Sat Jan 13 2024 10:14:17 GMT+0000 (Coordinated Universal Time)
cuid: clrbwua6c000108l052wwep1l
slug: how-to-send-application-logs-to-telegram-in-laravel
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705140998613/69747291-11c2-430e-8b9e-f57df276f84d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1705140641022/678fe30a-169b-40c0-9179-042c47eb3b7f.png
tags: laravel, php, telegram, laraveldevelopment, laravelframework

---

# How To Send Application Logs To Telegram Channel In Laravel

**Hello Web Artisans,**

Today's article will explore how to send application logs to a Telegram Channel using Laravel. But first, let's delve into the significance of logs in software development and why they're crucial for our work.

**Logging is an important aspect of SD because it helps the developers to understand why and where these errors or execution happening in the Application.**

## Logger and Logger Types in Laravel

**Laravel Logger -** This logger functionality works with different types of channel specification information.

**Laravel Logger Types** - The List of Error Types and Functions

| <mark>Logger Type</mark> | <mark>Logger Function</mark> |
| --- | --- |
| **Debug**: Used for detailed debug information | Log::debug("this is debug logger"); |
| **Info**: Used to log informational messages | Log::info('This is an informational message.'); |
| **Notice**: Used for normal but significant events | Log::notice('This is a notice message.'); |
| **Warning**: Used to indicate something unexpected that is not necessarily an error | Log::warning('This is a warning message.'); |
| **Error**: Used to record error events that might still allow the application to continue running. | Log::error('This is an error message.'); |
| **Critical**: Used for critical conditions, like serious errors that cause major disruptions. | Log::critical('This is a critical message.'); |
| **Alert**: Used to indicate that immediate action is required. | Log::alert('This is an alert message.'); |
| **Emergency**: Used to log system is unusable situations. | Log::emergency('This is an emergency message.'); |

**The accepted parameters in Laravel Logger Functions:**

* **message (string)** - The information about the logger types.
    
* **context** **(array)** - The message bind parameters in the logger.
    

## Create a Telegram Bot and Make An Admin in a Channel

The List Of Steps to create a telegram bot and make an admin channel

* Connect with **Telegram Bot Father** to create a Telegram Bot - **Search in the Telegram App To Find.**
    
* Select **start** command and create the bot.
    

![Connect with Telegram Bot Father to create a Telegram Bot](https://cdn.hashnode.com/res/hashnode/image/upload/v1705140726212/304e61a3-0739-4885-9c04-59b7253b7b09.png align="left")

* Select **newbot** command and give the name of the bot.
    
* Then set the username that ends with **\_bot.**
    
* **Get the Access Token for Future Use.**
    

![ newbot command and give the name of the bot](https://cdn.hashnode.com/res/hashnode/image/upload/v1705125122047/53479c17-f194-4d09-8724-1cc6d8991fe3.png align="left")

* Navigate to Profile and Click Create Channel
    
* Set The **Channel Name**, Description and Profile Pic(Optional)
    

![Create Telegram Channel in Profile Section](https://cdn.hashnode.com/res/hashnode/image/upload/v1705130612978/3dd9abbd-d6cd-4f33-8960-07e49bdb332d.png align="center")

* Click the create button and make the channel **if public or private.**
    
* Add the bot as member and **make an admin**
    

**In the channel Text the message "Hi".**

![Telegram Channel Created!](https://cdn.hashnode.com/res/hashnode/image/upload/v1705130926692/9f4b437b-5778-4726-8abb-be922325517f.png align="left")

## Integrate and Send Application Logs to Telegram

### Telegram Bot Configuration In Laravel Application Logging

<mark>In this section, we will walk through the process of setting up and integrating a Telegram bot for logging in a Laravel application, detailing each step along the way.</mark>

* **Add the Environment variables in .env .**
    
    ```yaml
    #.env
    TELEGRAM_API_KEY=Telegram-Access-Key
    TELEGRAM_CHANNEL=Channel-Id
    ```
    
* **Add the Logger Classes on top and Channel Configuration in logging.php** .
    
    ```php
    # config\logging.php
    <?php
    use Monolog\Handler\FilterHandler;
    use Monolog\Handler\TelegramBotHandler;
    ```
    
    ```php
    # config\logging.php
    <?php
            'stack' => [
                'driver' => 'stack',
                'channels' => ['single','telegram'],
                'ignore_exceptions' => false,
            ],
    #end of the array - add this channel
            "telegram" => [
                'driver'  => 'monolog',
                'handler' => FilterHandler::class,
                'level' => env('LOG_LEVEL', 'debug'),
                'with' => [
                    'handler' => new TelegramBotHandler($apiKey = env('TELEGRAM_API_KEY'), $channel = env('TELEGRAM_CHANNEL'))
                ]
            ],
    ```
    
* If Specific type of logger message only need set the `level => logger_type`
    
* Better Understanding go through this commit changes 🔽 Click the Below Link
    
* [Telegram Bot Configuration Commit Link](https://github.com/dhanar98/telegram-error-log-in-laravel/commit/ea568174313bfb179be26f2ed3d0dead2fe94cdc#diff-9ba917899def7f26cdd2c34da749863fbb2797a40aed5e41a1166a022b10d7df)
    
* Place the Telegram API Key and the Telegram Channel identifiers in the `.env` file.
    
* We have already obtained the Laravel API Key from the <mark>Bot Father Channel</mark>, which is now set in the `.env` file.
    
* The parameter for the Telegram channel can take either a <mark>string or an integer as its value.</mark>
    
* **if the channel is public set the value as channel username**
    
    ```yaml
    TELEGRAM_API_KEY=Telegram-Access-Key
    TELEGRAM_CHANNEL=@laravel_app_logger
    ```
    
* **If the channel is private get the channel id from the Telegram** `GetUpdates` **API URL.**
    
    ```yaml
    #https://api.telegram.org/bot{TELEGRAM_API_KEY}/getUpdates
    ```
    
* **{TELEGRAM\_API\_KEY} -** <mark>In this place add the API key and open the URL new tab in the browser.</mark>
    
* In the new tab get the channel id in the JSON with Bot Integrated Channel
    
    ```json
            "chat": {
              "id": "channel_id",
              "title": "Laravel-APP-Logger",
              "type": "channel"
            }
    ```
    
    <div data-node-type="callout">
    <div data-node-type="callout-emoji">💡</div>
    <div data-node-type="callout-text"><strong>NOTE:</strong></div>
    </div>
    
    Before hit this endpoint <mark>send the </mark> `"hi"` <mark>message in the channel and get the channel id</mark>
    
* **If the channel id is starts with minus it is private. if it is without minus it is public or use username**
    
* set the channel id in the `.env`
    
    ```yaml
    #IF public-channel
    TELEGRAM_CHANNEL=@laravel_app_logger
    #OR
    TELEGRAM_CHANNEL=12345678
    #IF PRIVATE CHANNEL
    TELEGRAM_CHANNEL=-12345678
    ```
    
* **Now we are ready to share the logs in telegram channel.**
    

```php
<?php
use Illuminate\Support\Facades\Log;

Log::error("error");
Log::debug("debug");
```

![Send Application Logs to Telegram Channel in Laravel ](https://cdn.hashnode.com/res/hashnode/image/upload/v1705135692828/c9e77c57-7558-43aa-98f2-bf462f23bca6.png align="left")

* [Tinker-Extension](https://marketplace.visualstudio.com/items?itemName=tinkerun.tinkerun-vscode) - Let's start running tinker in Visual Studio Code.
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>Reference Links</strong></div>
</div>

1. Laravel Logging - [https://laravel.com/docs/10.x/logging](https://laravel.com/docs/10.x/logging)
    
2. Explore Telegram Bot API's - [https://core.telegram.org/bots/api#chat](https://core.telegram.org/bots/api#chat)
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>PRO-TIP</strong></div>
</div>

### Send a Telegram Message using Custom Helper Function

The above Methods send telegram notification to application logs in the channel.

If you are planning to send other kind of notification in the channel <mark>use this helper function in for jobs , events and others.</mark>

%[https://gist.github.com/dhanar98/17e1c554db6bb6bc9bcd265b4cb4386f] 

* if multiple channels use this function to send message based on chat id and bot token.
    
* <mark>keep it safe the bot token and chat id for channel if it possible use encrypt and decrypt to processing the request.</mark>
    

**In conclusion, integrating Telegram with your Laravel application for sending logs is a powerful way to monitor your application’s health and activity in real-time. By leveraging the simplicity and effectiveness of Telegram bots, you can keep a close eye on your application's behavior, receive instant notifications of issues, and maintain a high level of operational awareness.**

I hope this article is helpful to all of you. follow and support 💜💜💜💰

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>Connect With Me:</strong></div>
</div>

<center>
[![Gmail](https://img.shields.io/badge/gmail-F44336?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dhanasekarravi98@gmail.com)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/dhanar98/)
[![Instagram](https://img.shields.io/badge/instagram-000?style=for-the-badge&logo=instagram&logoColor=ffd200)](https://www.instagram.com/dhanar.98/)
[![Whatsapp](https://img.shields.io/badge/WhatsApp-25D366.svg?style=for-the-badge&logo=WhatsApp&logoColor=white)](https://wa.me/9025165942/?text=hi%20%2C%20ping%20you%20from%20via%20hashnode%20blog)
</center>

%\[[https://www.instagram.com/p/C2DIL0WPTTC/?utm\_source=ig\_web\_copy\_link&igsh=MzRlODBiNWFlZA==](https://www.instagram.com/p/C2DIL0WPTTC/?utm_source=ig_web_copy_link&igsh=MzRlODBiNWFlZA==)\]