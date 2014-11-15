csc309-a3
=========

An online store for baseball cards

## Running Locally

Make sure you have PHP, Apache and Composer installed.  Also, install the [Heroku Toolbelt](https://toolbelt.heroku.com/).

```sh
$ composer update
$ foreman start web
```

Your app should now be running on [localhost:5000](http://localhost:5000/).

## Deploying to Heroku

```
$ heroku create
$ git push heroku master
$ heroku open
```
