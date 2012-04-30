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
 5. [Configurating your application](#guide-configure)
   1. [Configuration Formats](#guide-configure-1)
   2. [Contextual Configuration Loading](#guide-configure-2)
   3. [app.yml Configuration File](#guide-configure-3)
   4. [ioc.yml Configuration File](#guide-configure-4)
   5. [routing.yml Configuration File](#guide-configure-5)
 6. [Model-View-Controller Architecture](#guide-mvc)
   1. [Models](#guide-mvc-models)
     1. [Example](#guide-mvc-models-example)
   2. [Views](#guide-mvc-views)
     1. [Templates](#guide-mvc-templates)
     2. [Themes](#guide-mvc-themes)
   3. [Controllers](#guide-mvc-controllers)
 7. What's next?
 8. Glossary


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

 1. Open the `index.php` file, found in the root folder of your application, with your favourite PHP editor. The `index.php` file is called the Application Front Controller.
 2. Modify the `__PACKFIRE_PATH__` constant and set it to where you put your **packfire** framework folder.

>**Application Front Controller**: Packfire uses the Front Controller Pattern (FCP) to route all requests to the web application into a single file and hence allowing you to control all your URL routings through PHP without knowledge of writing and need to maintaining the `.htaccess` file. 

For example if I put my framework folder to 'C:\apps\packfire', I would set my `__PACKFIRE_PATH__` constant to 'C:\apps\packfire' and it would look like this:

    define('__PACKFIRE_PATH__', 'C:\apps\packfire');

###Installaton Done!

Congratulations! Now that you have completed the 3 steps of installation, you should be able to open Packfire on your browser and a welcome screen will show up:

>![Packfire Framework Welcome Screen](http://i.imgur.com/38nQw.png)  
Packfire Framework Welcome Screen

##<a name="guide-configure"></a>Configurating your application

Packfire Framework is designed to require minimal configuration and reduces the need for you to use the command line to perform configuration, tweaking and application hardening.

Your configuration files are found in the 'pack/config' folder. 

###<a name="guide-configure-1"></a>Configuration Formats

Packfire is currently able to read the following configuration formats:

 - YAML (*.yml, *.yaml)
 - INI Configuration File Format (*.ini)
 - PHP File that returns an array (*.php)

###<a name="guide-configure-2"></a>Contextual Configuration Loading

Packfire understands that your application will tend to go through several phases of design, development and testing and therefore will require very different configuration for each of the machine environment. 

In the Application Front Controller, there is a line that defines the `__ENVIRONMENT__` constant.

    define('__ENVIRONMENT__' , '');

You can modify the constant according to where the application is currently located. For example, 'local' for local development server and 'test' for the test server.

Whenever an environment is specified, the configuration file set for the environment will be loaded instead of the default one. For example if the environment is set to 'test', Packfire will look for and load 'app.test.yml' first. If the contextual configuration file is not found, it will fallback to load the default one, i.e. 'app.yml'.

###<a name="guide-configure-3"></a>app.yml Configuration File

`app.yml` configuration file contains the application, session and database configuration settings.
	
###<a name="guide-configure-4"></a>ioc.yml Configuration File

The `ioc.yml` configuration file sets all the services that will be loaded into the IoC Service Bucket whenever the application runs. These services will be accessible to all your controllers and classes use the IoC service bucket.

Each entry in the IoC configuration file is defined as:

	serviceName:
	  class: packageClassPath
	  parameters:
	    - param1
	    - param2

The service can then be loaded from the service bucket through `$this->service('serviceName')` in your controller or view. Any service loaded into the bucket that requires the use of the bucket will be provided the access to do so.

###<a name="guide-configure-5"></a>routing.yml Configuration File
You can manage all your URL route definitions in the `routing.yml` configuration file. An example of a route entry in the routing configuration file:

    home: 
      rewrite: "/"
      actual: "Home"
    themeSwitch:
      rewrite: "/theme/switch/{theme}"
      actual: "ThemeSwitch:switch"
      method: 
	- get
        - post
      params:
        theme: "([a-zA-Z0-9]+)"

- `themeSwitch`: this is the routing key, which uniquely identifies the routing entry.
- `rewrite`: the rewritten URL. You can enter parameters in the URL like templates.
- `actual`: The actual controller and action to be executed. You can leave out the "Controller" at the end of the class name. The `:` separates the class name and the action name. The action name is optional and if left out the default action name "index" is used.
- `method`: The HTTP method that the route is catered for. 
- `params`: The hash map of parameters with its regular expression.

The routing package in Packfire is powerful. Each parameter is parsed with regular expressions, which allows you to filter and validate your input data in the URL at the first stage.

##<a name="guide-mvc"></a>Model-View-Controller Architecture

Model-View-Controller (MVC) is a system architectural design that focuses on Separation of Concerns. MVC is commonly found in many frameworks and system, such as Microsoft .NET Framework, Java Server Pages and Symfony2 Framework. MVC helps to break down large web applications into smaller re-usable components so as to conform to the best practices of Object-Oriented Programming. No matter how big or small your application is, MVC is a good way to develop your application for scalability.

Packfire is designed to be a Push MVC framework. Take a look at the diagram below to understand how MVC is designed in Packfire.

![Packfire MVC Architectural Design](http://i.imgur.com/v7yGDl.png)

###<a name="guide-mvc-models"></a>Models

Models are classes that holds your application knowledge and data. They can form relationships between each other to make your application data more interesting. You can think of them as entities and objects that your controller can work on and manipulate.

>The model is a collection of classes that form a software application intended to store, and optionally separate, data.  
>  
> -- [Model–view–controller, Wikipedia](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)

####<a name="guide-mvc-models-example"></a>Example

For example, in the case of a web-based library, you may find the `Book` class as a Model for a physical book, storing the book title, `Author` object and ISBN number.

In Packfire, you can place your Models in the `pack/model` folder. This will allow your controller to load the models through the `model()` method. You can write the following code in your Controller to load your models.

    $instance = $this->model('Book');

Subsequently after loading the model, you can create additional instances through the standard PHP `new` keyword in your Controller:

    $this->model('Book');
    $book = new Book(); // Book is your model class placed as 'pack/model/Book.php'
    $book->title = $this->params()->get('title');
    $book->authorId = $this->params()->get('authorId');
    Book::save($book);

###<a name="guide-mvc-views"></a>Views

To help you manage your application's view classes easily, Packfire has included functionalities that allow you to create and reuse view. The `pView` abstract class prepares the data loaded by the controller for the template to parse.

The View component of Packfire separates your View manipulation logic and HTML code, which allows web designers and developers to work on front-end development with more ease and haste as PHP view formatting codes are isolated from the HTML code.

####<a name="guide-mvc-templates"></a>Templates

Packfire adopts the Mustache project for a logic-less template rendering engine by default. Writing templates for Packfire does not make things difficult for the designer and the developer, as the templates are clearly separated from the view logic. 

>![Packfire Moustache](http://i.imgur.com/HQo3a.png)  
> Packfire Moustache: lightweight logic-less template rendering engine.

You can read more about Mustache and how to use it through the Mustache [manual(1)](http://mustache.github.com/mustache.1.html) and [manual(5)](http://mustache.github.com/mustache.5.html) pages.

> Packfire calls for and has a strong stance on [View-Template Separation](http://packfire.tumblr.com/post/21211626941/view-template-separation). Read more about it on [our development blog](http://packfire.tumblr.com/).

You can set the template to render in your `pView` class by calling the `template()` method:

    $this->template(new pMoustacheTemplate($templateFile));

or if you use the `AppView` class:

    $this->template('userPage'); 
    // loads the template file at /pack/template/userPage.html

####<a name="guide-mvc-themes"></a>Themes

Packfire View Themes make it easy to switch your website's look and feel easily by implementing themes. You can switch themes for different occasions such as New Year, April Fool's, Halloween, Christmas, etc, or switch based on the user's colour preferences.

You can define your theme classes in the '/pack/theme' folder, extending from `pTheme`.

The concept is simple: All your themes will define the variables required to constitute your theme, for example background colour. So in your theme classes:

-- DarkTheme:

    $this->define('backgroundClr', '#666');
    $this->define('foregroundClr', '#FFF');

-- LightTheme:

    $this->define('backgroundClr', '#DDD');
    $this->define('foregroundClr', '#222');

To put these variables onto your template, simply use the `theme.{variable}` tags, for example using Moustache:

    <style type="text/css">
        body{
            background-color:{{theme.backgroundClr}};
            color:{{theme.foregroundClr}};
        }
    </style>

###<a name="guide-mvc-controllers"></a>Controllers

The controller is the heart of your web application. In your controllers lie the logic and actions that interact with the users' requests. You can use the routing functionalities to direct URL requests to controllers and its actions.

Controllers interact with your application models, database, users authentication, set data to views and implement functionalities for your application.