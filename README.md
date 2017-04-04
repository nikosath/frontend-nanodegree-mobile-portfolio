## Project Requirement \#1 (Critical Rendering Path)
`index.html` achieves a `PageSpeed` score of at least 90 for Mobile and Desktop.

## My Optimizations/Changes

#### Images

* Resized and/or recompressed all images that needed such treatment.

#### index.html

* Using the 'defer' keyword, I deferred the loading and execution of `analytics.js`, until after the initial render or other critical parts of the page have finished loading.
* Using `media = "print"`, I removed `print.css` from the CRP (Critical Rendering Path).
* I minified and inlined `style.css`.
* I deferred the `<link>` tag for google fonts, through the use of Javascript (`defer-css.js`).
* Inserted my Google Analytics profile ID (has nothing to do with performance).

## Results
Achieved 92 Mobile & 95 Desktop, PageSpeed Score ([link](https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fwww.nikosath.space%2Ffrontend-nanodegree-mobile-portfolio%2F&tab=desktop)).

## Project Requirement #2 (Frame Rate)

Optimizations made to `views/js/main.js` make `views/pizza.html` render with a consistent frame-rate at `60fps` when scrolling.

## My Optimizations/Changes

#### main.js


* global `items`
* var value1
