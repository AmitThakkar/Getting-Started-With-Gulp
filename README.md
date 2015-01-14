#Getting Started with GulpJS

####This repository contains Getting started guild with GulpJS.

Now a days, a **JavaScript** task runner is getting very famous. Yes, its name is **Gulp**. Many of us get confused between **Gulp** and **Grunt**. But why did I choose **Gulp**?

> **Gulp** is faster and simpler then **Grunt**. And I prefer **Gulp**, because we write **Gulp** tasks in **JavaScript** language, and as I am **JavaScript** lover + developer so I feel pretty happy and confident to write **Gulp** tasks. Trust me. if you are **JavaScript** developer/lover then you are going to love **Gulp** task runner.

We are not going to discuss **Gulp** vs **Grunt** in details. You will find loads of materials, which discuss **Gulp** vs **Grunt**. Here we will learn how to write **Gulp** tasks.

Lets first install **Gulp** into the system:

1. Install **Gulp** globally with command ```npm install -g gulp```. If you face permission error, run same command with sudo as ```sudo npm install -g gulp```.

2. Install **Gulp** into your project with command ```npm install --save-dev gulp```. If you face permission error, run same command with sudo as ```sudo npm install --save-dev gulp```.

**NOTE:** In your project directory, a ```node_modules``` named directory will be created after running the above command ```npm install --save-dev gulp```.

Now gulp will tell us what we have to do next, execute simply ```gulp``` command, it will print error **No gulpfile found**. Yup, that is our next step. Create an empty ```gulpfile.js``` file. Now again run ```gulp``` command, it will print error **Task 'default' is not in your gulpfile**. Lets create a default task in **gulpfile.js** as below:

**gulpfile.js**
```JavaScript
//  Requiring gulp
var gulp = require('gulp');
// Defining default task, which will execute when we simply type gulp.
gulp.task('default', function () {
    console.log("Hello from default gulp task.");
});
```

**Gulp** provides ```gulp.task()``` api to create custom tasks, first argument is name of task, and second argument can be task **function** or array of task **functions** which will be execute when that task will be executed.

When we type ```gulp``` command, then **Gulp** will execute task, which is followed by ```gulp``` command. e.g. ```gulp t1``` will execute **t1** named task. And if we do not provide any task name after ```gulp``` command then by default it executes **default** task. So when we were typing only ```gulp```, it was showing error message **Task 'default' is not in your gulpfile**.

Now type ```gulp``` or ```gulp default``` it will execute default task and will print our ```console.log```.

```Output
Using gulpfile ~/Projects/Getting-Started-With-Gulp/gulpfile.js
Starting 'default'...
Hello from default gulp task.
Finished 'default' after 100 μs
```

Lets write a custom task, which will first minify/compress all the ```.js``` files from js directory then store all minified/compressed files to build/js directive, and will watch all the js files which are present in js directory, if any change happens in those ```.js``` files, then it will re-minify/re-compress all the ```.js``` files, and overwrite all old minified/compressed files with latest minified/compressed files in build/js directory.

**Updated gulpfile.js**
```JavaScript
var gulp = require('gulp'),
    uglify = require('gulp-uglify');
function errorLog(error) {
    console.error(error);
    this.emit('end');
}
// Scripts Task
// Uglify
gulp.task('scripts', function () {
    gulp.src('js/*.js')
        .pipe(uglify())
        .on('error', errorLog)
        .pipe(gulp.dest('build/js'));
});
// Watch Task
// Watches JS
gulp.task('watch', function () {
    gulp.watch('js/*.js', ['scripts']);
});
gulp.task('default', ['scripts', 'watch']);
```

> **NOTE** We are using ```uglify``` **npm** module for minifying/compressing ```.js``` files. And it remove all comments and unused code from source **JavaScript** files.

In the above **gulpfile.js**, we have write 3 tasks:

1. **scripts:** This task is for minifying all the ```.js``` files from **js** directory, and store into **build/js** directory. We are handing **error** event and printing error on console, so **Gulp** does not stops, otherwise if there will be any error while minifying the ```.js``` files, **gulp** will give error and will get stopped.
2. **watch:** This task watches all the ```.js``` files from **js** directory, and any of the ```.js``` files get changed, it will execute **scripts** task.
3. **default:** This is our **default** task, which first executes **scripts** task and then **watch** task.

**Note**: If you want execute only **watch** task or  **scripts** task, then type ```gulp watch``` or ```gulp scripts``` respectively.

You can checkout full working source code from this [link](https://github.com/AmitThakkar/Getting-Started-With-Gulp).

You can read the next part of the series [here](http://codechutney.in/blog/nodejs/getting-started-with-gulp/).