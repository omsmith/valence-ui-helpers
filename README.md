#VUI Helpers

This project contains GULP helper scripts for building VUI components.

##Usage

Install as a development dependency:

```shell
npm install --save-dev vui-helpers
```

Then add it to your `gulpfile.js`:

```javascript
var vuiHelpers = require('vui-helpers');
```

##API

###clean

Deletes directories or files.

```javascript
gulp.task( 'clean', function() {
  return vuiHelpers.clean( [ 'dir1', 'dir2' ] );
} );
```

The only parameter is an array of directories/files to delete.

###makeCss

Performs a [lint](https://www.npmjs.org/package/gulp-csslint) of the CSS files
to validate syntax and CSS best practices, does a
[LESS compilation](https://www.npmjs.org/package/gulp-less) of any LESS files,
and finally [auto-prefixes](https://www.npmjs.org/package/autoprefixer) the CSS
to add vendor-specific prefixes based on our currently supported browsers.

```javascript
var vuiHelpers = require('vui-helpers');
gulp.task( 'css', function() {
  return vuiHelpers.makeCss( 'source/*', 'dist' );
} );
```

The first parameter is a glob which defines your CSS input files, followed by
an output directory.

###makeLess

Copies LESS files from source to target.

```javascript
var vuiHelpers = require('vui-helpers');
gulp.task( 'less', function() {
  return vui.makeLess( 'src/**/*.less', 'dist/' );
} );
```

The first parameter is a glob which defines the LESS input files, followed by
an output location.

###test

Helper for testing with [Karma](https://www.npmjs.org/package/gulp-karma).

```javascript
gulp.task( 'test', function () {
  return vui.test(
    'test/unit/karma.conf.js',
    'test/unit/**/*Spec.js',
    'dist/**/*.css'
  );
} );
```

The first parameter is the location of a karma configuration file, followed by
a glob which defines your test specs. The last parameter is a glob for any
CSS files to be included in the tests.