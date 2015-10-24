# Gulp


## Installation

1. Install gulp globally:

    $ npm install -g gulp

2. Initialize project as node module:

    $ npm init
    
3. Install gulp locally:

    $ npm install --save-dev gulp

4. Create an initial gulpfile.js:

```javascript
var project = require('./package.json');
var gulp = require('gulp');

gulp.task('default', function() {
    console.log('Building %s version %s', project.name, project.version);
});
```

## Sample Tasks

* Clean task:

```javascript
npm install --save-dev del

var del = require('del');

gulp.task('clean', function () {
    del([
        'dist'
    ]);
});
```

* CSS task:

```javascript
npm install --save-dev gulp-minify-css gulp-autoprefixer gulp-rename  

var minify = require('gulp-minify-css');
var rename = require('gulp-rename');
var prefix = require('gulp-autoprefixer');

gulp.task('css', function () {
    return gulp.src('src/css/main.css')
        .pipe(minify())
        .pipe(rename('main.min.css'))
        .pipe(prefix({
            browsers: ['last 2 versions', '> 2%'],
            cascade: false
        }))
        .pipe(gulp.dest('dist/css/'))
});
```

* JS task:

```javascript
npm install --save-dev gulp-concat gulp-uglify gulp-jslint

var jslint = require('gulp-jslint');
var concat = require('gulp-concat');
var uglify = require('gulp-uglify');

gulp.task('js', function () {
    return gulp.src('src/js/**/*.js')
        .pipe(jslint())
        .pipe(concat('main.min.js'))
        .pipe(uglify())
        .pipe(gulp.dest('dist/js/'));
});
```

* HTML task:

```javascript
npm install --save-dev gulp-htmlbuild gulp-htmlclean

var htmlbuild = require('gulp-htmlbuild');
var htmlclean = require('gulp-htmlclean');

gulp.task('html', function () {
    return gulp.src('src/*.html')
        .pipe(htmlbuild({
            js: htmlbuild.preprocess.js(function (block) {
                block.write('js/main.min.js');
                block.end();
            }),
            css: htmlbuild.preprocess.css(function (block) {
                block.write('css/main.min.css');
                block.end();
            })
        }))
        .pipe(htmlclean())
        .pipe(gulp.dest('dist'))
});
```

* Images task:

```javascript
npm install --save-dev gulp-imagemin

var imagemin = require('gulp-imagemin');

gulp.task('images', function () {
    return gulp.src('src/images/*.png')
        .pipe(imagemin())
        .pipe(gulp.dest('dist/images/'));
});
```
