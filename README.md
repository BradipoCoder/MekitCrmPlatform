CRM Application Skeleton
=========================

This is the application skeleton that will host the following main components:

* Symfony 2
* Oro Platform
* Mekit CRM

After installation you will have a fully working CRM application using the above mentioned main components.

## Requirements

* PHP 5.4.9 or above with command line interface(CLI)
* PHP Extensions
    * GD
    * Mcrypt
    * JSON
    * ctype
    * Tokenizer
    * SimpleXML
    * PCRE
    * ICU
* MySQL 5.1 or above OR PostgreSQL 9.1 or above

## Installation instructions

### Install and update Composer

Make sure you have an updated and working composer installation. If this is not the case or you do not know what composer is then 
 please refer to the instructions on http://getcomposer.org.

- In short, you can grab it by typing:
```
    curl -s https://getcomposer.org/installer | php
```

- Make sure composer is in your path and update it by typing:
```
    php composer.phar selfupdate
```
To spin up the process it can take some time because composer must calculate the dependencies for the packages.
Just be patient.

### Download Mekit CRM Platform and Mekit CRM Application
 
Go to the directory where you want to install the project an launch the install process:

```
    php composer.phar create-project mekit/crm-platform
```

This will download the Mekit CRM platform and automatically install all required dependencies.

When all packages have been downloaded the installer will ask you the following questions and you need to provide the
answers for them. In the parenthesis you will find the default answer to the question so if it satisfies you, just press \<Enter\>:

- database_driver (pdo_mysql): You can use MySql(pdo_mysql) or PostgreSQL(pdo_pgsql)
- database_host (127.0.0.1): The ip address of your database server deployment
- database_port (null): The port on which database server communicates. If you are using the predefined port just press \<Enter\>
- database_name (null): The name of your database. This database must exist.
- database_user (null): The username to use to authenticate against the database server
- database_password (null): The password to use to authenticate against the database server
- mailer_transport (mail): You will configure this later, so just press \<Enter\>
- mailer_host (127.0.0.1): You will configure this later, so just press \<Enter\>
- mailer_port (null): You will configure this later, so just press \<Enter\>
- mailer_encryption (null): You will configure this later, so just press \<Enter\>
- mailer_user (null): You will configure this later, so just press \<Enter\>
- mailer_password (null): You will configure this later, so just press \<Enter\>
- websocket_host (127.0.0.1): You will configure this later, so just press \<Enter\>
- websocket_port (8080): You will configure this later, so just press \<Enter\>
- session_handler (session.handler.native_file): just press \<Enter\>
- locale (en): just press \<Enter\>
- secret (ThisTokenIsNotSoSecretSoChangeIt): just press \<Enter\>
- installed (null): just press \<Enter\>

All this information you have just typed in has now been saved into the file "app/config/parameters.yml" inside your project folder.
You can make modifications to it manually before proceeding to the next step.

When the installation has terminated you will find the application inside a folder named "crm-platform". You can freely
rename and move this folder.

### Run the installation process

Enter the project directory:

```
cd crm-platform
```

and launch the installation process by using the CLI console command:

```
php app/console oro:install --env prod
```

The installer will run requirements checks on your system and if all is ok it will proceed with the installation. If there
are unmet requirements, the installer will tell you what problems you've got and it will halt. You will need to satisfy
all requirements before you will be able to proceed by relaunching the same console command.

After the installer has populated your database with tables and initial data, it will pause to ask you a few questions.
As before, you will need to provide the answers:

- Application URL (http://localhost/oro/): The URL from which the application will be accessible
- Organization name (ORO): The name of your organization 
- Username (admin): The username of the administrator
- Email: The email of the administrator
- First name: The first name of the administrator
- Last name: The last name of the administrator
- Password: The password of the administrator
- Load sample data (y/n): Normally you'd say 'n'. Some bundles provide sample data for demonstration purposes, 

The installer will run for another while to create and optimize some client side resources (css, js) and it will finally
finish by saying: 'Oro Application has been successfully installed in prod mode.'


### Set up web server

The proper configuration of your web server is out of the scope of this guide but to get you up and running it it should be
sufficient to set up a virtual host serving files from the subdirectory "web" under your project root. The '.htaccess' file
inside this folder will instruct your Apache web server to serve the 'app.php' file automatically. 

There are lots of ways to configure Apache or Nginx (these are the most recommended ones)  so this giude will not provide
configuration instructions for them. The important thing is to set the base directory of your vhost to the
"[project directory]/web" folder.

Please refer to: http://symfony.com/doc/2.3/cookbook/configuration/web_server_configuration.html

## Advanced configuration (to be written)

- Enable WebSockets messaging

```bash
php app/console clank:server --env prod
```

- Configure crontab for automatic execution of scheduled commands:

```bash
php app/console oro:cron --env prod
```
 
**Note:**  The above command must be put into your crontab manually (write this...). 

## Notes (to be written)

...