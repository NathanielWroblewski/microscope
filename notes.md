Notes
===

New app
---
```sh
$ mrt create app_name
$ cd app_name
$ meteor
```

Add [Atmosphere](https://atmosphere.meteor.com/) package
---
```sh
$ mrt add bootstrap
$ mrt add coffeescript
```

Add smart package
---
```sh
$ meteor add underscore
```

Open Local Mongo console
---
```sh
$ meteor mongo
$ mrt mongo
> db.posts.insert({title: 'A new post'})
> db.posts.find();
```

Open remote mongo console (if hosted on meteor.com)
---
```sh
$ meteor mongo app_name
```

Reset database
---
```sh
$ meteor reset
```


Deploy as meteor subdomain
```sh
$ meteor deploy app_name.meteor.com
$ meteor deploy app_name.meteor.com -p
```

Deploy with modulus
```sh
$ npm install -g modulus
$ modulus login
$ modulus env set MONGO_URL "mongodb://<user>:<pass>@mongo.onmodulus.net:27017/<database_name>"
$ modulus deploy
```

Deploy on own server (Digital Ocean or AWS) using Meteor Up
```sh
$ npm install -g mup
$ mkdir ~/microscope-deploy
$ cd ~/microscope-deploy
$ mup init
$ mup setup
$ mup deploy
$ mup logs -f
```
mup.json holds deployment-related settings
settings.json holds app-related settings (OAuth tokens, analytics tokens, etc.)

Template
---
List
```html
<template name="postsList">
  {{#each posts}}
    {{> postItem}}
  {{/each}}
</template>
```

Item
```html
<template name="postItem">
  <a href="{{url}}">{{title}}</a>{{domain}}
</template>
```

Controller
---
List
```js
Template.postsList.helpers({
  posts: [{url: ... },...]
});
```

Item
```js
Template.postItem.helpers({
  domain: function() {
    var a = document.createElement('a');
    a.href = this.url;
    return a.hostname;
  }
});
```



