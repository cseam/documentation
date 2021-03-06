---
title:  How to develop on local
date:   2015-11-27 11:11:00
categories: Development
tags: Development
permalink: /how-to-develop-local/
keywords: test, dev, license, host, theme
---
If you want to develop your theme on local, you can do it by using reoc.lo as hostname. In this way, you will not require an extra license to develop your theme locally.

This guide provides the information you need for that!

## Requirements

At first, you need to check the needed requirements to run Yclas Self Hosted:

+ A computer that has a working internet connection
+ An internet browser
+ A web hosting that supports:
  * Apache 2+
  * PHP 5.6+
  * Short Tags
  * GD support
  * mod_rewrite
  * mcrypt
  * Gettext
  * Curl
  * MySQL 5+

## Vhost

Secondly, create a vhost called 'reoc.lo'; this will enable debug/profiler tools, disable cache and disable minify.

To create this vhost open /etc/hosts file with a text editor:

    sudo vim /etc/hosts

and add this line below _127.0.0.1   localhost_:

    127.0.0.1   reoc.lo


Next, a file called reoc.lo.conf into /etc/apache2/sites-available/:

    sudo vim /etc/apache2/sites-available/reoc.lo.conf

you can use the following:

    <VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName reoc.lo
        ServerAlias www.reoc.lo
        DocumentRoot /var/www/yclas
        <Directory "/var/www/yclas">
            AllowOverride All
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>


Save it and enable the site:

    sudo a2ensite reoc.lo
    sudo service apache2 reload

## Install Yclas Self Hosted and use your premium theme

Now you have reoc.lo activated! The last step is to install Yclas Self Hosted following [this guide](http://docs.yclas.com/install-self-hosted/). Note that if you used the above reoc.lo.conf file, you have to install Yclas Self Hosted into /var/www/yclas.

To use your premium theme go to your panel Appearance -> Theme, choose to activate your theme and enter a valid or invalid license number.


You can now develop your theme on local!


<br>
**Related guides:**

+ [Vagrant configuration for Yclas Self Hosted]({{ site.baseurl }}/vagrant-configuration)
+ [Docker configuration for Yclas Self Hosted]({{ site.baseurl }}/docker-image)