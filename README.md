# CSS Pre-Processor Lesson
Let's first dive into a little background.
##### What is a Pre-Processor?
A pre-processor is a program that takes one type of data and converts it to another. So some common pre-processor you've probably seen....

* JavaScript
  * CoffeeScript, LiveScript, TypeScript and Babel

* HTML
  * Markdown, HAML, Slim and Jade

  #####  & CSS Pre-Processors..

  * [SASS](http://sass-lang.com/guide)
    * Converts .scss to .css
	* Ability to **store variables**. Ex: Colors or fonts you use often
	```
	$font-stack:    Helvetica, sans-serif;
	$primary-color: #333;
	```
	* **Nesting**, so you can create a visual hierarchy
	* **Partials**, **Imports**, **Mixins**, **Extends** and **Operators** which we will go over later more in depth.
  * [LESS](http://lesscss.org/features/)
    * Converts .less to .css
	* Strongest competitor to SASS right now.
  * [Stylus](http://stylus-lang.com/)
    * Omit Brackets & much more!
  * Others Include:
    * [CSS-Crush](http://the-echoplex.net/csscrush/)
	* [Myth](http://www.myth.io/)
	* [Rework](http://www.myth.io/)




### Instructions
Now, let's dive in on how to get SASS up and running.
1. [Install SASS](http://sass-lang.com/install)
 * **Linux Users** try ```sudo su -c "gem install sass"```
  * **Windows Users** - Install Ruby using [Ruby Installer](http://rubyinstaller.org/).
  * **Mac Users** - You already have Ruby!
  * In your terminal type ``` gem install sass ```, if you encounter an error, try it with sudo ``` sudo gem install sass ```.
  * Check your version by typing ```sass -v```, you should have Sass 3.4.22

2. Now, let's have some fun. Create a stylesheet.css and stylesheet.scss in the dist folder.
3. Create an index.html, and link your **css** to it.
4. Now, let's make SASS watch the changes to the **scss** file and convert them to **css**.
5. Let's create a script that will remember those pathways. First run ``` npm init ``` in the terminal. Go into your package.json and under scripts add this line under the test ```,"convert-styles": "sass --watch dist/stylesheet.scss:dist/stylesheet.css"```
6. Close out the first SASS watch you have open by pressing CTRL+C, and then type ```npm run convert-styles```. You can edit the script files at any time, or name them to your preference.

### Features of SASS
Now, let's learn a little bit about why SASS is so cool...
#### 1. Variables
  * Let's say you have a specific font you want to use over and over again, or a color. You can use define those with SASS using a $ to define it. Let's try it now
  ```
  $primary-fontcolor: rgb(107, 124, 64);
  $primary-font: Helvetica, sans-serif;

  body {
	  font: $primary-font,
	  color: $primary-fontcolor
  }
  ```

#### 2. Nesting
  * Let's create a div inside a div on the index.
  ```
  <div class="testing">
		<div class="inside-testing">
			hi from inside div1
		<div>
  </div>
  ```
  Now on our .scss file we can single out the inside-div1 with nesting..  
  ```
  .testing {
  	.inside-testing {
  		font-size: 5em;
  	}
  }
  ```


#### 3. Importing/Patrials
  * You can create partials using import when you want to split up your scss into smaller parts.
  * Let's create a really basic div to show partials and imports in the index.html, for example:
  ```
  <div class="fake-nav">
	  <ul>
		  <li>HOME</li>
		  <li>LOGIN</li>
	  </ul>
  </div>
  ```
  * Now, create a file named **nav.scss**, inside of that file style your new fake nav bar. I've styled mine this way...
  ```
  .fake-nav {
  	height: 150px;
  	width: 100%;
  	background: rgb(44, 142, 175);
  }
  ```
  * Notice how these styles are not currently being used? Well they're not hooked up anywhere yet. Let's change that by importing your **nav.scss** into your **stylesheet.scss**. Do this by-
  ```
  @import 'nav';

  ```
  at the top of your **stylesheet.scss** file.

#### 4. Mixins
  * Mixins allow you to easily write the same bit of CSS over and over again just by using the word include. Let's say your website has various size boxes, but they're all styled the same. A Mixin would be a of great use in this situation. **Add the following divs to your index**.
  ```
  <div class="square1">

  </div>
  <div class="square2">

  </div>
  ```
 * Now, on your stylesheet.scss, let's create a mixin to style these.
 ```
 @mixin style-box($length-width, $color) {
	 height: $length-width;
	 width: $length-width;
	 background-color: $color;
 }
 ```
 * Now, let's style square1 and square2
 ```
 .square1 {@include style-box(40px, rgb(184, 53, 158))}
 .square2 {@include style-box(100px, rgb(81, 70, 83))}

 ```


#### 5.Extend/Inheritance

 * Extend allows you to use the same exact line of css with another class in css.

 ```
 .message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}
```

#### 6. Operators
* Last, but not least. Operators. SASS allows you to do math inside of you SCSS with ``` +, -, * & %```.
```
.fake-nav {
	width: 100% / 2;
}
```
