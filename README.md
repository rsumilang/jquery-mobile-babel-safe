jquery-mobile-babel-safe
========================

This is a ready to use version of jQuery mobile that should work fine if you are
doing any transpiling.

# Install

NPM:

    npm install jquery-mobile-babel-safe --save

Update *package.json*:

    "browser": {
      "jquery-mobile": "./node_modules/jquery-mobile-babel-safe/dist/jquery.mobile.js"
    },
    "browserify-shim": {
      "jquery-mobile": {
        "exports": "jQuery.mobile"
      }
    }

# The Quick Fix

This solves the *undefined* `this` variable in jQuery mobile by explicitly
using the `window` object.

*Original IIFE*

```
(function($, window){
  // code
})(jQuery, this)
```

*Updated IIFE*

```
(function($, window){
  // code
})(jQuery, this || window)
```

# Why?

Most of the solutions out on the web have a tricks to make this work with CJS
but not so much with babel. I needed a quick way to make this work for a project
so I just added the above little hack for now which seems to be safe.

I will update this project once there is a better way to work with jQuery mobile
and babel.

For now, at least I get to stay stick with `npm` :)

# License

USE AT YOUR OWN RISK.
