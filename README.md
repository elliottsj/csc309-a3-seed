csc309-a3
=========

An online store for baseball cards

## Running locally

You'll need these requirements:

- [PHP ~5.6.2](http://php.net/)
- [Apache httpd ~2.4.10](http://httpd.apache.org/)
- [MySQL ~5.6.21](http://www.mysql.com/)
- [Composer ~1.0.0-alpha8](https://getcomposer.org/)
- [foreman](https://github.com/ddollar/foreman)

Start your MySQL server, then run the following:

```shell
composer install
export DATABASE_URL=""
php -S localhost:4000
```

Your app should now be running on [localhost:5000](http://localhost:5000/).

#### Complete setup on OS X

Here is how to set up your development environment on OS X:

###### Install Homebrew

If you don't already have Homebrew installed, go to <http://brew.sh> to install it.

###### Install PHP, Apache, MySQL, and Composer

```shell
# Add extra repositories
brew tap homebrew/dupes
brew tap homebrew/php
brew tap homebrew/apache

brew install --with-fpm php56  # Install PHP
brew install httpd24           # Install Apache httpd
brew install mysql             # Install MySQL
brew install composer          # Install Composer
```

Locate the following lines in `/usr/local/etc/apache2/2.4/httpd.conf`:

```
...
#LoadModule proxy_module libexec/mod_proxy.so
#LoadModule proxy_connect_module libexec/mod_proxy_connect.so
#LoadModule proxy_ftp_module libexec/mod_proxy_ftp.so
#LoadModule proxy_http_module libexec/mod_proxy_http.so
#LoadModule proxy_fcgi_module libexec/mod_proxy_fcgi.so
...
```

And uncomment the `mod_proxy` and `mod_proxy_fcgi` lines:

```
...
LoadModule proxy_module libexec/mod_proxy.so
#LoadModule proxy_connect_module libexec/mod_proxy_connect.so
#LoadModule proxy_ftp_module libexec/mod_proxy_ftp.so
#LoadModule proxy_http_module libexec/mod_proxy_http.so
LoadModule proxy_fcgi_module libexec/mod_proxy_fcgi.so
...
```

To start your MySQL server, run the following:

```
mysql.server start
```

###### (Optional) Install XDebug

```
pecl install xdebug
```

Add this to the end of `/usr/local/etc/php/5.6/php.ini`:

```
[xdebug]
; The location of the installed XDebug shared lib
zend_extension="/usr/local/Cellar/php56/5.6.2/lib/php/extensions/no-debug-non-zts-20131226/xdebug.so"
; Enable the debugger
xdebug.remote_enable=1
```

## Deploying to Dokku

https://console.aws.amazon.com/ec2/home?region=us-east-1#launchAmi=ami-9eaa1cf6

```
$ heroku create
$ git push heroku master
$ heroku open
```
