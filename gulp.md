# Gulp


## Installation

1. Install gulp globally:

    $ npm install -g gulp

2. Initialize project as node module:

    $ npm init
    
3. Install gulp locally:

    $ npm install --save-dev gulp

4. Create an initial gulpfile.js:

```
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

gulp.task('css', function () {
    return gulp.src('app/css/main.css')
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

gulp.task('js', function () {
    return gulp.src('app/js/**/*.js')
        .pipe(jslint())
        .pipe(concat('main.min.js'))
        .pipe(uglify())
        .pipe(gulp.dest('dist/js/'));
});
```
