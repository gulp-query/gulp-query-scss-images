## gulp-query-scss-images
SCSS + sprites and assets

Uses [gulp-css-spritus](https://github.com/nurieff/gulp-css-spritus) and 
[gulp-css-assetus](https://github.com/nurieff/gulp-css-assetus) for images

Uses [cssnano](http://cssnano.co/) with autoprefixer for optimization

* This plugin provides automatic source maps, compiling Sass into CSS, autoprefixing and minification.
* Write your CSS rules without vendor prefixes — autoprefixer will do everything itself.
* Make sprites easily
* Compress images directly in the `.scss`

```
npm install gulp-query gulp-query-scss-images
```

### Example
Paste the code into your `gulpfile.js` and configure it
```javascript
let build = require('gulp-query')
  , scss = require('gulp-query-scss-images')
;
build(function (query) {
    query.plugins([scss, webpack])
      .scss('src/scss/app.scss','css/','app')

      .scss('src/scss/admin.scss','css/undercover.css',{
        includePaths: [
          ...
        ]
      })

      .scss({
        from: 'src/scss/main.scss',
        to: 'css/',
        name: 'main'
      })
      ;
});
```
And feel the freedom
```
gulp
gulp --production // For production
gulp watch // Watching change
gulp scss // Only for scss
gulp scss:app // Only for app.scss
gulp scss:admin scss:main watch // Watching change only for admin.scss and main.scss
...
```

### Options
```javascript
.scss({
    name: "new_name", // For gulp scss:new_name 
    from: "scss/app.scss",
    to: "css/",
    source_map: true,
    source_map_type: 'inline',
    full: false, // if set true is without compress in prod
    image_dir_css: '../images/', // for css (image-url) 
    image_dir_save: 'images/', // for save image assets. Relative path from gulpfile.js 
    includePaths: [
        //'../node_modules/compass-mixins/lib/', // relative path from gulpfile.js 
    ],
    autoprefixer: {
      browsers: ["> 1%", "last 2 versions"],
    },
    png: {
      quality: '60-70',
      speed: 1
    },
    jpeg: {
      quality: 60,
    }
})
```