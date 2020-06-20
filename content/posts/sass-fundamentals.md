---
title: "Sass Fundamentals"
date: 2020-06-20T12:03:36+08:00
tags: []
draft: false
---

### Prerequisite and introduction

- Install [Node.js](https://nodejs.org/en/)
- There are two types of file extension of Sass called **.sass** and **.scss**
- **.scss** is preferred over **.sass** as it uses the same syntax as regular css
- **npm install node-sass**
- Add the following scripts in package.json
- **sass: "node-sass -w scss/ -o dist/css/ --recursive"**
- Create a sass file **main.scss** in the scss directory
- Create dist folder in project root directory
- All the compiled scss will go into dist folder
- Run **npm run sass**
- Link **css/main.css** in your html
- If preferred a GUI application over a terminal, [Koala](http://koala-app.com/) is a GUI application for Sass compilation. Download and install, drag your project into it, and change the output directory for the compiled scss
- Create partials, **_variables.scss**, which tell scss compiler don't compile this file
- Import the partials in main scss file, **@import 'variables';**

### SASS fundamentals

Variables
```css
$primary-color: steelblue
$secondary-color: skyblue
$dark-color: #333
$light-color: #f4f4f4

body { 
  background: $color;
}
```

Nesting
```html
<div class="section">
  <div class="section-a">
    <p>Hello World</p>
  </div>
  <div class="section-b">
    <p>Hello World</p>
  </div>
  <a href="">Read More</a>
</div>
```
```scss
.section {
  &-a {
    color: #fefefe;
  }

  &-b {
    color: #333;
  }

  a {
    color: #333;

    &:hover {
      color: #000
    }
  }
}
```

**&** represent the parent selector's name

Inheritance
```scss
%btn-shared {
  display: inline-block;
  padding: 0.5rem 1rem;
  border: none;
  text-decoration: none;
}

.btn {
  &-dark {
    @extend %btn-shared;
    background-color: $dark-color
    color: $light-color
  }

  &-light {
    @extend %btn-shared;
    background-color: $light-color
    color: $dark-color
  }
}
```

Functions
- Create a partials, **_functions.scss**
```scss
@function set-text-color($bg-color) {
  @if(lightness($bg-color) > 50) {
    @return #333;
  }@else {
    @return #fff;
  }
}
```

```scss
#header {
  background: $dark-color;
  color: set-text-color($dark-color);
}
```