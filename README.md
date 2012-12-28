# Wordpress2Tumblr

## Migrate all posts from WordPress to Tumblr

Does what it should. However, some things are still messy:

* Tags are not preserved
* Categories are not preserved

## How to run

Prereq: I'm assuming you can run php scripts from your local machine. Here's a [helpful guide I found for enabling it on OS X](http://foundationphp.com/tutorials/php_leopard.php).

### Preparation

1. Export (just) the posts from your WordPress blog. You will end up with a XML-File.
2. If you have more than 200 posts, you need to split the file as tumblr does not allow to post more than 200 posts per day. A good tool to split up WordPress XML-files (on a Mac) is [WordPress WXR file splitter for Mac OS X](http://suhastech.com/wordpress-wxr-xmlfile-splitter-for-mac-os-x/). There are--I am sure--numerous splitters for users of other operating systems. Use Google. (For splitting, I suggest you use a file size of 1MB as this most likely does not include more than 200 posts...)
3. Get the WordPress2Tumblr code from the [GitHub project page](https://github.com/mkalina/Wordpress2Tumblr) and place it on your server.
4. Copy the XML-Files you created with the splitter into the same directory on your server.

### Registering WordPress2Tumblr on Tumblr.

1. Go to [http://www.tumblr.com/oauth/apps](http://www.tumblr.com/oauth/apps) and click on "Register Application".
2. Give the app whatever name you like.
3. Set the callback URL to the directory you have saved WordPress2Tumblr on your server.
4. Copy down the Consumer and Secret key to a safe place.

### Preparing connect.php

* Set the Consumer Key.
* Set the Consumer Secret.
* Set the Callback URL.

### Preparing callback.php

* Set the Consumer Key.
* Set the Secret Key.
* Set the full path to the (first split up) WordPress Export file.
* Set the tumblr name of the tumblelog you want to import into (eg. mygreattumblr.tumblr.com)

### And Action!

1. Open `connect.php` on your webserver in your browser.
2. This will direct you to Tumblr asking to authorize the application.
3. Click Yes, and you're redirected back to the `callback.php` file.
4. Wait. (`callback.php` is now reading your entries from the XML-file you specified and positing them to tumblr).

If everything works fine, you will get an ugly formatted but readable list of post titles and dates of the first XML-files' posts. Repeat the process (starting from "Preparing callback.php") with the next XML-files' file name _the next day_ (this is forced by tumblr's api).


## History

This is a fork from Ryan Galgons WordPress2Tumblr-project that I hope will someday be available as a WordPress plugin.

This is a kludge, joining these 2 bits of code and some minor updates:
* [Tumblr Oauth example from lucasec](https://groups.google.com/d/msg/tumblr-api/g6SeIBWvsnE/gnWqT9jFSlEJ)
* [wp-tumblr.php script](http://sourcecookbook.com/es/recipes/73/how-to-export-wordpress-posts-to-tumblr) 
