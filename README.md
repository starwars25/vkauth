# VK Auth
## Description

This module for [Express.js](http://expressjs.com/) will help you get server [VK](http://vk.com) access token. After that you can use it to create your authentication system which uses **VK**. After gaining access token you can use it in other **VK API** modules. You can also easily get OAuth URL based on your settings with handy `getUrl()` method. 

## Installation

Clone repository, copy `vkauth.js` to your project.

Soon the package will be avalable on **npm**.

## Configuring

Example of using:

```
var vkauth = require('./vkauth');
vkauth.config.client_id = Number(process.env['VK_CLIENT_ID']);
vkauth.config.app_secret = process.env['VK_APP_SECRET'];
vkauth.config.host = 'localhost:3000';
vkauth.config.route = '/token';
vkauth.config.scope = ['friends'];
```

Description:

* `client_id` - Client Id of your app;
* `app_secret` - Secret key of your app;
* `host` - Host of your application;
* `route` - Route where you want to get access token;
* `scope` - Array of permissions of your app.

You also can specify version of API using `v` property. Set it as `String`.

## Using

Example:

```
vkauth.start(app, function(res, err, token) {
    if (err) {
        console.log(err);
    } else {
        console.log(token);
        res.json(token);
    }
});
```

* `app` - `Express.js` instance;
* `res` - `Response` object;
* `err` - Error, will be `null` if there is no error;
* `token` - `access_token` object, will be null, if there is an error.

`token` object:

* `token.access_token` - access token;
* `token.user_id` - user id;
* `token.expires_in` - expiration time in seconds.

You can get **VK API URL** based on `config` object using method `vkauth.getUrl()`.
