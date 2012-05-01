#Starters' Guide to Packfire Framework for PHP

**Authors**:

  - Sam-Mauris Yong &lt;mauris@hotmail.sg&gt;

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
 6. [Programming in Packfire](#guide-programming)
   1. [Integrated Development Environment / Editor](#guide-ide)
   2. [Development Standards](#guide-standards)
     1. [PHP File Formatting](#guide-formatting)
     2. [Naming Convention](#guide-naming)
   3. [Class Loading](#guide-class-loader)
   4. [In-Code Documentation](#guide-code-help)
 7. [Model-View-Controller Architecture](#guide-mvc)
   1. [Models](#guide-mvc-models)
     1. [Modelling Your Application](#guide-mvc-modelling)
     2. [Model Tips](#guide-mvc-modeltips)
   2. [Views](#guide-mvc-views)
     1. [Templates](#guide-mvc-templates)
     2. [Themes](#guide-mvc-themes)
   3. [Controllers](#guide-mvc-controllers)
     1. [Controller Actions](#guide-mvc-actions)
     2. [Model and View](#guide-mvc-model-view)
     3. [State Transference](#guide-mvc-state)
 8. What's next?
 9. Glossary


##<a name="guide-preface"></a>Preface

**Thank you** for taking time to start on your development journey with Packfire Framework for PHP.

In this book *Starters' Guide to Packfire Framework for PHP*, you can expect great help and guidance to get you started in developing your application for the vast cloud and network of Internet. The purpose and goal of this book is simple:

>To get developers started on building web and back-end applications using Packfire Framework and PHP Programming Language.  

This book requires you to have some form of knowledge and basic foundation of programming to be able follow smoothly. If you come from another programming language (such as C#, Java or Python), you will progress much faster with your current programming knowledge. 

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

>![Downloading Packfire from Github.](http://i.imgur.com/sDAktl.png)  
>Downloading Packfire from Github.

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

>![Packfire Framework Welcome Screen](http://i.imgur.com/L1UpEl.png)  
>Packfire Framework Welcome Screen

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

Whenever an environment is specified, the configuration file set for the environment will be loaded instead of the default one. For example if the environment is set to 'test', Packfire will look for and load 'app.test.yml' first. If the contextual configuration file is not found, it will load the default one, i.e. 'app.yml'.

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
- `actual`: The actual controller and action to be executed. You can leave out the "Controller" at the end of the class name. The `:` separates the class name and the action name. The action name is optional and if left out the default action name "index" is used
- `method`: The HTTP method that the route is catered for
- `params`: The hash map of parameters with its regular expression

The routing package in Packfire is powerful. Each parameter is parsed with regular expressions, which allows you to filter and validate your input data in the URL at the first stage.

##Programming in Packfire

There are several things you should take note when programming in Packfire as it may be a little different from your preferred language or framework. As you go through the topics in this chapter you will feel more comfortable developing your application.

###Integrated Development Environment / Editor

An Integrated Development Environment, or IDE for short, is application that aids you in your software development cycle. As there may be many things to handle, an IDE helps you to break down your software project for easier management.

While usage of an IDE is be subjected to your preference, it is still recommended that an IDE is used when in development of a software application as it reduces chances of silly bugs, provides tools and features that speeds up development and helps you in debugging.

Packfire was developed with the great help of NetBeans IDE. You can use any PHP IDE or editor of your choice. 

###<a name="guide-standards"></a>Development Standards

Conforming to standards of development helps everyone to understand each other's code better. Sometimes bugs and problems are easily caused by a small naming problem in the code and takes hours to be discovered. It is therefore of more efficiency that a standard way of development is published and adhered to. 

####PHP File Formatting

PHP files in Packfire are to be strictly used for PHP codes. No HTML or whitespaces must be embeded outside of the PHP code is allowed. PHP files must start with `<?php` and the trailing `?>` is not permitted. Short PHP tags or ASP-style tags are not allowed.

It is recommended that the maximum length of your lines should be at 80 characters. You should break for a new line if your line exceeds 80 characters. In NetBeans and most IDE, a line is shown at the end of the 80th character to indicate the limit.

Indentation must be of 4 spaces. Tabs messes up codes across platforms.

Only one class per file is allowed. Functions are to be declared in a separate PHP file from the classes.

####Naming Conventions

Naming convention sets the style of naming our files, classes, interfaces, methods, functions, variables, constants etc. Packfire follows a naming convention close to Java, C# and Zend that is easily adaptable by users widely. Naming has to be meaningful, descriptive and easily understandable by others. 

  - **Classes**
    - Camel Casing with first letter in upper case singular, e.g. `PdfReader`, `BookListView`, `HtmlValidator`, `Debugger`
    - Framework classes follow the above rule, and are prefixed with a lower case 'p' singular, e.g. `pApplication`, `pDateTime`, `pDebuggerOutput`
  - **Interfaces**
    - Camel Casing with first letter in upper case and prefixed with upper case 'I' singular, e.g. `IRunnable`, `ILinq`, `IHtmlOutput`
  - **Files**
    - PHP class: Exact name as the class that the file is holding.
    - PHP misc: Camel casing with first letter in lower case, singular.
    - Other files: Camel casing with first letter in lower case.
    - Folders: Camel casing with first letter in lower case, singular.
  - **Methods and Functions**
    - Camel Casing with first letter in lower case, e.g. `renderOutput`, `verifyUser`, `runCode`
  - **Variables**
    - Camel Casing with first letter in lower case, e.g. `state`, `pointData`, `tableBuffer`
  - **Constants**
    - All in upper casing with underscore breaking the words, e.g. `STATUS_DENIED`, `TYPE_FULL`, `ORANGE`
    - Packfire constants follow the above rule, and are indicated with a double underscore prefix and suffix, e.g. `__ENVIRONMENT__`, `__PACKFIRE_ROOT__`

Camel Casing refers to naming convention that requires each word in the name to have its first letter in upper case, example: CopyFiles, HtmlCode, JavaScript. 

###Class Loader

Packfire uses the `pClassLoader` class to load files and classes.  However, a helper function `pload` was created to assist in the loading of classes.

At the top of your PHP files, you can write the `pload()` statements to load the classes that your class in that file will use or depend on by supplying the package and class name. 

>If your class is in `/pack/library/mailer/SmtpMailer.php`, the full package name would be `library.mailer.SmtpMailer`. However if the class you want to load is from the Packfire Framework, you have to append the `packfire.` in front, e.g. `packfire.plinq.pLinq`. 

Once advantage is that pload allows you to supply wildcards to load multiple classes in one statement. For example, `library.drivers.*Driver` would load all classes in the '/pack/library/drivers' folder with name that ends with 'Driver'.

###In-Code Documentation

Packfire classes and methods contains in-code PHPDoc documentation that you have access to. In NetBeans IDE, as you type along, documentation shows up to tell you what parameters, for example, are for the method you are writing. 

##<a name="guide-mvc"></a>Model-View-Controller Architecture

Model-View-Controller (MVC) is a system architectural design that focuses on Separation of Concerns. MVC is commonly found in many frameworks and system, such as Microsoft .NET Framework, Java Server Pages and Symfony2 Framework. MVC helps to break down large web applications into smaller re-usable components so as to conform to the best practices of Object-Oriented Programming. No matter how big or small your application is, MVC is a good way to develop your application for scalability.

Packfire is designed to be a Push MVC framework. Take a look at the diagram below to understand how MVC is designed in Packfire.

>![Packfire MVC Architectural Design](http://i.imgur.com/v7yGDl.png)  
>Packfire's Push MVC Architectural Design

###<a name="guide-mvc-models"></a>Models

Models are classes that holds your application knowledge and data. They can form relationships between each other to make your application data more interesting. You can think of them as entities and objects that your controller can work on and manipulate.

>The model is a collection of classes that form a software application intended to store, and optionally separate, data.  
>  
> -- [Model–view–controller, Wikipedia](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)

####<a name="guide-mvc-modelling"></a>Modelling Your Application

It is good practice that you break down your application for high cohesion in classes and low coupling between classes (the concept of OOP). Identifying key models in your application can help you to reduce your coding time, prevent potential bugs and loopholes and ease debugging.

For example, in the case of a web-based library, you may find the `Book` class as a Model for a physical book, storing the book title, `Author` object and ISBN number.

In Packfire, you can place your Models in the `pack/model` folder. This will allow your controller to load the models through the `model()` method. You can write the following code in your Controller to load your models.

    $instance = $this->model('Book');

####<a name="guide-mvc-modeltips"></a>Model Tips

If you are using LINQ to build your database queries (i.e. the `IDbLinq` class), you make your model class an instance of the `packfire.database.pDbModel` class and supply your model into the LINQ query through the `model()` method. This will help you define all the columns and properties mapping in the query.

    $availableBooks = $this->service('database')->from('books')
                ->model($this->model('Book'))
                ->where('quantity > :quota')
                ->param('quota', 5)
                ->fetch();

Subsequently after loading the model, you can create additional instances through the standard PHP `new` keyword in your Controller:

    $this->model('Book');
    $book = new Book(); // Book is your model class placed as 'pack/model/Book.php'
    $book->title = $this->params()->get('title');
    $book->authorId = $this->params()->get('authorId');
    Book::save($book);

###<a name="guide-mvc-views"></a>Views

To help you manage your application's view classes easily, Packfire has included functionalities that allow you to create and reuse view. The `pView` abstract class prepares the data loaded by the controller for the template to parse.

The View component of Packfire separates your View manipulation logic and HTML code, which allows web designers and developers to work on front-end development with more ease and haste as PHP view formatting codes are isolated from the HTML code.

You can write your view rendering logic in and by overriding the `create()` method of your view class. Call the `define()` to set values to your template tags.

    class BookListView extends AppView {
        protected function create() {
            $theme = $this->service('session')->get('theme', 'dark');
            if(!in_array($theme, array('dark', 'light'))){
                $theme = 'light';
            }
            $this->template('BookList')->theme($theme);
            
            $this->define('title', 'Book List');
            $this->define('books', $this->state['books']);
            
            $this->filter('title', 'htmlentities|trim');
        }
    }

> A sample View class in Packfire

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

**Dark Theme**:

    $this->define('backgroundClr', '666');
    $this->define('foregroundClr', 'FFF');

**Light Theme**:

    $this->define('backgroundClr', 'DDD');
    $this->define('foregroundClr', '222');

To put these variables onto your template, simply use the `theme.variable` tags, for example using Moustache:

    <style type="text/css">
        body{
            background-color: #{{theme.backgroundClr}};
            color: #{{theme.foregroundClr}};
        }
    </style>

###<a name="guide-mvc-controllers"></a>Controllers

The controller is the heart of your web application. In your controllers lie the logic and actions that interact with the users' requests. Controllers interact with your application models, database, users authentication, set data to views and implement functionalities for your application. You can use the routing functionalities to direct URL requests to controllers and its actions. 

In your Packfire Application, controllers classes are placed in the '/pack/controller' folder and all controllers extend from the `AppController` class.

####<a name="guide-mvc-actions"></a>Controller Actions

Application and business logic are all placed within actions of the controller. For each of your action, you will need to give a name to it. For example, the Book controller may have the actions `view` for viewing details on a book, `list` for listing all the books, `create` for adding a new book and `delete` for removing a book.

Actions are, simply put, methods of your controller class. Their names are prefixed by `do` (i.e. `doView`, `doList`, `doCreate`, `doDelete`) and can be accessed by any HTTP request methods.  

The prefix can also be the HTTP methods that can access it. For example you can define the method `getDelete()` to display a confirmation page on the deletion of a book and the method `postDelete()` to actually delete the book and redirect the user back to the book list page.

>Packfire is RESTful. In the routing configuration, you can determine what HTTP request methods your action can be called be called from. For example, you can define that `create` can be only accessed by HTTP POST. 

####<a name="guide-mvc-model-view"></a>Model and View

Since Controller contains the application and business logic in your application, it has the right to use, mold and manipulate the other components of the architecture: Model and View. 

Earlier on we said that you can load models through the `model()` method in controllers:

    $this->model('Book');

The `model()` method will include the file (in this case '/pack/model/Book.php') and create a new instance. The instance would then be stored in the controller. The next time you call the `model()` method it will return you the stored instance, unless the reload parameter is set to `true`.

Once you are done with your controller action, you can load the view by calling the `render()` method in your controller:

    $this->render(new BookListView()); // BookkListView is an instance of the pView

You can also let the `render()` method to automatically load the view class by not passing any parameters. The controller will then look for a view class with the matching controller and action name in the view folder.

For example if your controller is 'Book' and your action is 'List', the controller will look for:

  - /pack/view/book/BookListView.php
  - /pack/view/BookListView.php

####<a name="guide-mvc-state"></a>State Transference

In your controller, there is a property called `$state`. The state property allows you to store information that is automatically transferred to your View when the `render()` method is called. You can store, for example, an array of books that is to be displayed by the View.

##What's Next?

##Glossary
