# Front-end Nanodegree Project: Website Optimization

For this project I had to optimize a provided website with a number of
optimization and performance related issues.

## Usage

You may visit `index.html` at the
[github project page](http://www.nikosath.space/udacity-frontend-nanodegree-mobile-portfolio/),
or head straight to the [pizza section](http://www.nikosath.space/udacity-frontend-nanodegree-mobile-portfolio/views/pizza.html).
As an alternative, you could download/clone the repo files and open
`index.html` in your favorite browser. Then you may open Chrome dev tools and
record a Timeline while scrolling those pizzas. It's smooth alright!
Also, try resizing the pizzas and notice the console log messages.
Finally, here's the [PageSpeed Score](https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fwww.nikosath.space%2Ffrontend-nanodegree-mobile-portfolio%2F&tab=desktop).
## Project Requirement \#1 (Critical Rendering Path)
`index.html` achieves a `PageSpeed` score of at least 90 for Mobile and Desktop.

### My Optimizations/Changes

#### Images

* Resized and/or recompressed all images that needed such treatment.

#### index.html

* Using the `defer` keyword, I deferred the loading and execution of
`analytics.js`, until after the initial render or other critical parts of the
page have finished loading.
* Using `media = "print"`, I removed `print.css` from the CRP (Critical
  Rendering Path).
* I minified and inlined `style.css`.
* I deferred the `<link>` tag for google fonts, through the use of Javascript
(`defer-css.js`).
* Inserted my Google Analytics profile ID (has nothing to do with performance).

### Results
Achieved 92 Mobile & 95 Desktop, PageSpeed Score ([link](https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fwww.nikosath.space%2Ffrontend-nanodegree-mobile-portfolio%2F&tab=desktop)).

## Project Requirement #2.1 (Frame Rate)

Optimizations made to `views/js/main.js` make `views/pizza.html` render with a
consistent frame-rate at `60fps` when scrolling.

### My Optimizations/Changes

#### main.js

* I reduced the number of elements with class `.mover`, i.e the moving pizzas,
from 200, to the exact number that the user will actually be able to see
(in my case 24). This was done by taking into account the browser window
viewport height.
* Inside the body of `updatePositions()`, I moved the calculations of
`document.body.scrollTop / 1250` and those of the 5 phases, outside of the
`for` loop they were in.
* I moved selectors such as `querySelectorAll`, outside of loops/functions in
order to prevent the unnecessary reuse of them. Furthermore, I ended up
replacing them, with the more performant variants `getElementsByClassName`
and `getElementsById` [(see)](https://jsperf.com/getelementbyid-vs-queryselector/25).

### Results
Achieved consistent frame-rate at `60fps` when scrolling `views/pizza.html`.

## Project Requirement #2.2 (Computational Efficiency)

Time to resize pizzas is less than `5ms` using the pizza size slider on the
`views/pizza.html` page. Resize time is shown in the browser developer tool console.

### My Optimizations/Changes

#### main.js

* I moved the calculations of `dx` and `newwidth` outside the `for` loop they were in.
* I moved the selector for elements of class `randomPizzaContainer` outside the
`for` loop, and replaced it with the more performant `getElementsByClassName`.

### Results
Achieved resize time of `1ms` or less.
