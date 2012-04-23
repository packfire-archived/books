#Starters' Guide to Packfire Framework for PHP

**Authors**:

  - Sam-Mauris Yong &lt;mauris*@*hotmail.sg&gt;

**Status**: Work-In-Progress  

**For Versions**: 1.0-sofia

Copyright © 2010-2012, Sam-Mauris Yong. All rights reserved. 

This work is digitally released in the form of a computer file under the [Creative Commons Attribution-NonCommercial-NoDerivs 3.0 Unported License](http://creativecommons.org/licenses/by-nc-nd/3.0/). Redistribution of this file through digital means is permitted provided that this copyright notice, license notice and this paragraph is retained in the copies.

##Content

 1. [Preface](#guide-preface)
 2. [Introduction](#guide-intro)
 3. [Requirements](#guide-require)
 4. [Installing Packfire](#guide-install)
   1. [Downloading Packfire](#guide-install-1)
   2. [Copying Files](#guide-install-2)
   3. [Setting Framework Path](#guide-install-3)
 5. Configurating your application
 6. Model-View-Controllers
   1. Controllers
   2. Views
   3. Models


##<a name="guide-preface"></a>Preface

**Thank you** for taking time to start on your development journey with Packfire Framework for PHP.

In this book *Starters' Guide to Packfire Framework for PHP*, you can expect great help and guidance to get you started in developing your application for the vast cloud and network of Internet. The goal of this book is simple:

>To get developers started on building web and back-end applications using Packfire Framework and PHP Programming Language.  

This book requires you to have some form of knowledge and basic foundation of programming to be able follow smoothly. If you come from another programming language (such as C#, Java or Python), you will be able to progress much faster with your current programming knowledge set. 

##<a name="guide-intro"></a>Introduction

Packfire is a clean and well thought web framework for developers of all walks to scaffold and bring up websites quickly and hassle-free. 

>You'll be surprised at how fast you can build a web application with a pack of fire.

A framework provides a well-designed and structured way to develop applications and also provide libraries of functionalities that you can use off the shelf to improve your development efficiency. In the context of Packfire, it helps you to write PHP with ease taking advantages of what the programming language has already been offering. Packfire also offers you a great sum of libraries and functionalities you can use in your application.

As Packfire facilitates Object-Oriented Programming (OOP), coming from an OOP language would be greatly beneficial to your learning process.

##<a name="guide-require"></a>Requirements

Packfire Framework relies on several other software and components to work on your server or computer. Without meeting the following criteria, Packfire cannot run your application properly.

 - A Web Server capable of running PHP (e.g. Apache HTTP Server, Lighttpd, IIS)
 - PHP Hypertext Preprocessor (PHP) 5.3.1 or higher
 - mod_rewrite needs to be enabled

As you go along, you may require more software and components than what Packfire offer. For example, a database is not included in Packfire and you may need to use one (such as MySQL, SQLite, Redis, OrientDB). A driver is often then required in order for Packfire to link your application to the database.

##<a name="guide-install"></a>Installing Packfire

Installing Packfire Framework involves 3 simple steps to follow:

###<a name="guide-install-1"></a>Step 1 - Downloading / Cloning

Download a copy of the `.zip` or `.tar.gz` archive of the entire `master` branch code base from Github `packfire/framework` in the Downloads section.

>![Downloading Packfire from Github.](http://i.imgur.com/sDAkt.png)  
Downloading Packfire from Github.

Alternatively, you can also clone the repository from Github by running the following Git command:

    git clone git@github.com:packfire/framework.git

###<a name="guide-install-2"></a>Step 2 - Copying Files

After you have downloaded a copy of the repository, there are two folders in the repository you need to take note of:

  - **packfire**: consists of the framework itself
  - **public**: your application structure and a demo-application inside

Copy the **packfire** folder and its content to a non-public location (e.g. 'C:\packfire' or '/usr/local/packfire'). 

Then, copy the application structure of the **public** folder to your web server's document root folder (`htdocs`, `public_html` etc.). You can put it in sub-folders of your web-server document root folder instead of the root-folder itself.

###<a name="guide-install-3"></a>Step 3 - Setting the Framework Path

 1. Open the `index.php` file, found in the root folder of your application, with your favourite PHP editor. 
 2. Modify the `__PACKFIRE_PATH__` constant and set it to where you put your **packfire** framework folder.

For example if I put my framework folder to 'C:\apps\packfire', I would set my `__PACKFIRE_PATH__` constant to 'C:\apps\packfire' and it would look like this:

    define('__PACKFIRE_PATH__', 'C:\apps\packfire');

###Installaton Done!

Now that you have completed the 3 steps of installation, you should be able to open Packfire on your browser and a welcome screen will show up:

>![Packfire Framework Welcome Screen](http://i.imgur.com/38nQw.png)  
Packfire Framework Welcome Screen