#Installation of Packfire Framework for PHP

**Author(s):**

- Sam-Mauris Yong (@thephpdeveloper)
- Yuki Matsukura (@matsubo)

**For version(s):**

 - 2.0


*Copyright (c) 2012, Sam-Mauris Yong.*  
This work is originally released digitally under the *Creative Commons Attribution-NonCommercial-NoDerivs 3.0 Unported License*. Redistribution of this file through any means is permitted only provided that the copyright and this license notice are retained in all copies. 

##Introduction

This book documents the installation procedure for Packfire Framework onto any PHP-supported system such as Windows, Macintosh or Linux. 

##Prerequisites

Since version 2.0 onwards, Packfire was re-designed to be [Composer](http://getcomposer.org) centric. The old method of using submodules made the repository difficult to maintain and versioning was bad, and hence it was decided that Composer was used to put components together.

Before installing Packfire, ensure that you familiarize yourself with Composer for a little. Composer comes in the form of a [phar binary](http://php.net/manual/en/intro.phar.php), which you can download from the website and run it with PHP. 

##Installing Packfire Framework

There are two methods of installing Packfire Framework for your applications:

1. **Composer Installation**: perform installation via Composer on the application and will be per-application basis.
2. **Global Installation**: download and install one copy of Packfire Framework for PHP and link all applications on the system to this installation.

Read on to the following section on elaborated details on how to install Packfire.

###Composer Installation

Installation of the Framework for your Packfire application through the use of Composer allows you to reap several benefits including:

- Seamless installation process through CLI
- Quick update process
- Version compatibility checks

To install Packfire Framework through Composer:

1. Download a copy of the Packfire Framework application structure from the [Github repository](https://github.com/packfire/app-structure).
  > You can either directly `git clone` then checkout a tag or click on "Tags" on the repository page and download the version you want to use.

2. Execute command `php composer.phar install` on the `pack` folder of your application, where the `composer.json` file resides, to install Packfire Framework for your application.

###Global Installation

Packfire Framework can be installed globally on a system for access by one or more, if not all, Packfire applications on that system.

To install Packfire Framework globally:

1. Download a copy of Packfire Framework from the [Github repository](https://github.com/packfire/packfire-framework).
  > You can either directly `git clone` then checkout a tag or click on "Tags" on the repository page and download the version you want to use.

2. Extract the contents to any readable part of your system. 

3. Execute command `php composer.phar install` in the root folder, where the `composer.json` file resides, to install Packfire Framework's dependencies, using Composer. 

4. Download a copy of the Packfire Framework application structure from [the Github repository](https://github.com/packfire/app-structure).
  > You can either directly `git clone` then checkout a tag or click on "Tags" on the repository page and download the version you want to use.

> Note that if you install Packfire Framework globally, you will be able to update the Framework through Composer. Updating will require a manual download and extraction similarly to the installation process. However, components used by Packfire Framework can still be updated through a Composer update done on the Framework itself. 


##Setting up Packfire application structure

1. Rename file from `pack/constants.php.dist` to `constants.php` and set the constant `__PACKFIRE_ROOT__` to the `src` folder of Packfire Framework.
```
mv pack/constants.php.dist pack/constants.php
vi pack/constants.php
```

2. You will need a writable permisison by the owner of web server.
```
chmod -R 777 pack/storage
```

3. Configure the URL of the application.
Set the top of the `app-structure` on the `app.rootUrl` key.
```
vi pack/config/app.yml
```


##Completed Installation


Upon completing the installation of your Packfire application and the Framework, the Welcome page should show up when you access top of the `app-structure` directory, showing the version number of Packfire Framework installed on the top right corner. You can combine a mix of Global and Composer installation processes depending on your needs for the application.

![](http://i.imgur.com/CVoxh.png)

Now that you have installed Packfire Framework and your application, you may go forth and write great code and applications.
