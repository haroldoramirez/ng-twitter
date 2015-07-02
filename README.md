[![Build Status](https://travis-ci.org/saimon24/ng-twitter.svg?branch=master)](https://travis-ci.org/saimon24/ng-twitter)

# ngTwitter

ngTwitter is an AngularJS [Twitter REST API](https://dev.twitter.com/rest/public) wrapper.  The purpose of this library is to quickly and easily access all the Twitter API endpoints without having to worry about the request signing and signature.


## Requirements

You need to have a Twitter app and a valid OAuth token.


## Installing ngTwitter

### Bower

Add this repository as dependency:

    $ bower install ng-twitter-api --save

This will add the dependency to your project and to the `bower.json` file.

The JavaScript library must then be added to your **index.html** file found in your projects **www**
directory:

    <script src="../ng-twitter/dist/ng-twitter.min.js"></script>

Twitter requires HMAC-SHA1 signatures in their Oauth implementation. Including the sha1.js component of jsSHA for this:

    <script src="../sha1.js"></script>

* [jsSHA 1.6.0](https://github.com/Caligatio/jsSHA) Secure Hash Library

### Injecting:

Once added to your index.html file, you must inject the library into your **app.js** module.  Make your
**app.js** file look something like the following:

    angular.module('starter', ['ngTwitter'])

Now ngTwitter is ready to use!

## Using ngTwitter In Your Project
1. Find your **ClientId** and your **SecretId** from your [Twitter app](https://apps.twitter.com/).
2. Grab you OAuth token inside your app. If you are using the [Ionic Framework](http://ionicframework.com/) you should use the [ngCordova](http://ngcordova.com/) library. After including it, your request for a OAuth token could look like this:
```javascript
    $cordovaOauth.twitter(clientId, clientSecret).then(function (succ) {
        $twitterApi.configure(clientId, clientSecret, succ);
      }, function(error) {
        console.log(error);
    });
```
*If you got your OAuth token differently, just make sure to configure ngTwitter before making any other calls like this:*
```javascript
    $twitterApi.configure(clientId, clientSecret, oauthToken);
```
After configuring you can use all the endpoint wrapper. Each API call returns a promise. The success callback is the complete Twitter Rest response.
```javascript
    $twitterApi.getHomeTimeline().then(function(data) {
      console.log(data);
    }, function(error) {
      console.log('err: ' + error);
    });
````


## Contribution Rules

All contributions must be made via the `development` branch.  This keeps the project more maintainable in terms of versioning as well as code control.


## Have a question or found a bug?

Message me on Twitter - [@schlimmson](https://www.twitter.com/schlimmson)

Follow my Blog Devdactic - [https://devdactic.com](https://devdactic.com)
