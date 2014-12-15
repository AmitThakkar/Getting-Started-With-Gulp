#Getting Started with Gulp

####This repository contains getting started guild with Gulp.

Now a days, a **JavaScript** task runner getting very famous. Yes that is **Gulp**. Many of us confuse between **Gulp** and **Grunt**. But why did I choose **Gulp**?

> **Gulp** is faster and simpler then **Grunt**. And I prefer **Gulp**, because we write **Gulp** tasks in **JavaScript** language, and as I am **JavaScript** lover + developer so I feel pretty happy and confident to write **Gulp** tasks. Trust me. if you are **JavaScript** developer/lover then you are going to love **Gulp** task runner.

We are not going to discuss **Gulp** vs **Grunt** in details. You will find lots of blog, which discuss **Gulp** vs **Grunt**. Here we will learn how to write **Gulp** tasks.

Lets file install **Gulp** into the system:

1. Install **Gulp** globally with command ```npm install -g gulp```. If you facing permission error, run same command with sudo as ```sudo npm install -g gulp```.

2. Install **Gulp** into your project with command ```npm install --save-dev gulp```. If you facing permission error, run same command with sudo as ```sudo npm install --save-dev gulp```.
NOTE: In your project directory, a ```node_modules``` named directory will be created after running the above command ```npm install --save-dev gulp```.

Now gulp will say what we have to do next, execute simply ```gulp``` command, it will print error **No gulpfile found**. Yup, that is our next step. Create a empty ```gulpfile.js``` file. Now again run ```gulp``` command, it will print error **Task 'default' is not in your gulpfile**. Yup, that is our next step, lets create a default task in **gulpfile.js** as below:

**gulpfile.js**
```
//  Requiring gulp
var gulp = require('gulp');
// Defining default task, which will execute when we type simply gulp.
gulp.task('default', function () {
    console.log("Hello from default gulp task.");
});
```

**Gulp** provide ```gulp.task()``` api to create custom tasks, first arguments is name of task, and second argument can be task **function** or array of task **function** which will be execute when that task will be execute. When we type ```gulp``` command, then **Gulp** will execute task, which is followed by ```gulp``` command. e.g. ```gulp t1``` will execute t1 named task. And if we do not provide any task name after ```gulp``` command then by default it execute **default** task. So when we were typing only ```gulp```, it was showing error message **Task 'default' is not in your gulpfile**.

Now type ```gulp``` or ```gulp default``` it will execute default task and will print our ```console.log```.

```
Using gulpfile ~/Projects/Getting-Started-With-Gulp/gulpfile.js
Starting 'default'...
Hello from default gulp task.
Finished 'default' after 100 μs
```

