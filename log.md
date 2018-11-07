# Learning log

|Date | since 28 Oct 2018 |
|:---:|:---------------------------------------|
|Content|Learnt, thoughts, progress, ideas, links|


----------------------------------------------------------  

## 6 Nov 2018 - Day 10

JavaScript - Coded 'Expense Tracker' along with Udemy JS course

:new: Started [freeCodeCamp JavaScript course](https://learn.freecodecamp.org/)! 
Such a nice learning resource!

- Learned : use case of querySelector, addEventListener, good use of 'target'
- Challage unsolved : how to sort the array in an alphabetical order, which has been sorted by boolean.

### Best error of today 
```JavaScript
const body = document.querySelector('body')
const button = document.querySelector('button')

button.addEventListener('click', function (e) {
    e.textContent = 'hahaha'
})
```

### Solved Challenge 01
When: 5 Nov 2018  
What: To deleted filtered items(elements that have the same value).  
How: Used _forEach_ instead of _.filter_
```JavaScript
const deleteIncomplete = function (array) {
    array.forEach(function (todo, index) {
        if(todo.completed) {
            array.splice(index, 1)
        } 
    })
}
deleteIncomplete(todos)
console.log(todos)
```
\
\
\

----------------------------------------------------------  
## 6 Nov 2018 - Day 10

JavaScript - Coded 'Expense Tracker' along with Udemy JS course

:new: Started [freeCodeCamp JavaScript course](https://learn.freecodecamp.org/)! 
Such a nice learning resource!

- Learned : use case of querySelector, addEventListener, good use of 'target'
- Challage unsolved : how to sort the array in an alphabetical order, which has been sorted by boolean.

### Best error of today 
```JavaScript
const body = document.querySelector('body')
const button = document.querySelector('button')

button.addEventListener('click', function (e) {
    e.textContent = 'hahaha'
})
```

----------------------------------------------------------



## 5 Nov 2018 - Day 9

JavaScript - messed around with methods, did related exercies

- Learned : Array seaching - indexOf(), .find(), .findIndex(), .filter()
- Self Challage 01 unsolved : ~~deleting filtered items from array~~ :round_pushpin:[solved](#Solved-Challenge-01).

----------------------------------------------------------



## 4 Nov 2018 - Day 8

JavaScript - 

- Learned : Object reference, string/number methods, 
			array methods to manipulate items
		    restaurant seat checker, number guessing game

- I really like this JS logic world. :D


----------------------------------------------------------



## 3 Nov 2018 - Day 7

JavaScript - 

- Learned : object, object as an argument of function, 
			function returning an object,

- It's ok not to understand it at once. It's ok. Keep calm and just try it again.

----------------------------------------------------------



## 2 Nov 2018 - Day 6

JavaScript - variable scope, return, object in function, access to property

- Built [To-do list](https://codepen.io/wonma/pen/jegdPW)(2nd) with cleaner code.

- Built [Gradient Generator](https://wonma.github.io/Background-generator)

- Feeling more and more used to making mistakes and finding solutions.

----------------------------------------------------------



## 1 Nov 2018 - Day 5

JavaScript DOM manipulation - selectors / events / callback functions

- Rebuilt mini facebook again. (Rebuilding till I feel comfortable!)

- Built [To-do list](https://codepen.io/wonma/pen/jegdPW) (Yay! Finally!!.. but need to go over it till I get it firmly.)

- var JavaScript.attribute = "magical";

----------------------------------------------------------



## 31 Oct 2018 - Day 4

Reviewed and finished exercises of Javascript Basics

- Learned [falsy values](https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a)

- Enjoyed coding [console version of mini facebook](https://codepen.io/wonma/pen/LgwPdv) while practicing flexbox.

- Learned the importance of of varible scope from my code error!
  [local vs. global variable](https://www.quora.com/What-happens-when-you-don%E2%80%99t-declare-a-variable-in-Javascript)

- Let's keep calm and practice again. :P

----------------------------------------------------------



## 30 Oct 2018 - Day 3

Finished analyzing the usage of Flexbox in the layout of the sample website.
- Flexbox has power in aligning items in one line.
- It's pretty much controlling how to manipulate the available space.
- Useful for responsive layout. 

Learned basic strategies about SEO(meta description, backlink), Image Optimization.

Resumed Andre's Javascript course.
- Created [robot movement](https://codepen.io/wonma/pen/XxLNxo).


----------------------------------------------------------



## 29 Oct 18 - Day 2

Reviewed command line basics.
- Figured out (AGAIN) the importance of distinguishing between relative paths and absolute paths.
- Understood what is home directory and root directory in perspective of terminal.

Set up browserSync package from scratch.
- Made it possible to watch multiple html docs (with separate tasks).
- Set up a basic startup working file.

Played with Flexbox.
- Tried to figure out how flexbox works.
- Analyzed structure of [the sample website](https://wonma.github.io/trillo/) I built a month ago, focusing primarily on the usage of flexbox. (halfway done.)

As far as I figured, Flexbox is generally about how you put things in "one line" either in a row or in a column. It's like a column flex in a row flex in a column flex etc...


----------------------------------------------------------



## 28 Oct 18 - Day 1

Working on [Sample Travel Site](https://github.com/wonma/travel-site) from this great Udemy course, [Git a Web Developer Job](https://www.udemy.com/git-a-web-developer-job-mastering-the-modern-workflow/) by Brad Schiff.

Succesfully Finished deploying [the Travel Site](https://wonma.github.io/travel-site/) following the course! 


----------------------------------------------------------


