# Learning log

|Date | since 28 Oct 2018 |
|:---:|:---------------------------------------|
|Content|Learnt, thoughts, progress, ideas, links|


----------------------------------------------------------  
## 14 Nov 2018 - Day 17

### JavaScript - with [the Modern JavaScript Bootcamp 2018](https://www.udemy.com/modern-javascript/)

- Learned : continued building notes-app & todos-app.  
	    improved the features with id(using uuid) / location.assign / complex DOM structure
 
### My Code vs. Better Code

A. My code (I used findIndex)
```JavaScript
    const checkTodoId = todos.findIndex(function (todo) {
        return todo.id === id
    }) 
    if(!todos[checkTodoId].completed){
        todos[checkTodoId].completed = true
    } else {
        todos[checkTodoId].completed = false
    }
```  
See how simple my teacher made the conditional statement.  
  
A. Teacher's code (He used 'find' method)
```JavaScript
    const todoToCheck = todos.find(function (todo) {
        return todo.id === id
    })
    if(todoToCheck !== undefined) {
        todoToCheck.completed = !todoToCheck.completed
    }
```
---

B. My code (I used if statement **to give true if the result is true lol**)

```JavaScript
   checkboxEl.setAttribute('type', 'checkbox')
   if (eachTodo.completed === true) {
       checkboxEl.setAttribute('checked', true)
   }
```

B. Teacher's code (He used the fact that **they both return boolean values** )

```JavaScript
   checkboxEl.setAttribute('type', 'checkbox')    
   checkboxEl.checked = eachTodo.completed
```

&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 13 Nov 2018 - Day 16

### JavaScript - with [the Modern JavaScript Bootcamp 2018](https://www.udemy.com/modern-javascript/)

- Learned : continued building notes-app & todos-app.  
	    Syncing data across pages / JS date () / moment js /  
	    integrating dates into the app (sort by recency or last edition)
 
### My Code vs. Better Code



A. My code (I used findIndex)
```JavaScript


```  
See how simple my teacher made the conditional statement.  
  
A. Teacher's code (He used 'find' method)
```JavaScript
    const todoToCheck = todos.find(function (todo) {
        return todo.id === id
    })
    if(todoToCheck !== undefined) {
        todoToCheck.completed = !todoToCheck.completed
    }
```
---

B. My code (I used if statement **to give true if the result is true lol**)

```JavaScript
   checkboxEl.setAttribute('type', 'checkbox')
   if (eachTodo.completed === true) {
       checkboxEl.setAttribute('checked', true)
   }
```

B. Teacher's code (He used the fact that **they both return boolean values** )

```JavaScript
   checkboxEl.setAttribute('type', 'checkbox')    
   checkboxEl.checked = eachTodo.completed
```

&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 12 Nov 2018 - Day 15

### JavaScript - with [the Modern JavaScript Bootcamp 2018](https://www.udemy.com/modern-javascript/)

- Learned : continued building notes-app & todos-app.  
	    improved the features with id(using uuid) / location.assign / complex DOM structure
 
### My Code vs. Better Code

A. My code (I used findIndex)
```JavaScript
    const checkTodoId = todos.findIndex(function (todo) {
        return todo.id === id
    }) 
    if(!todos[checkTodoId].completed){
        todos[checkTodoId].completed = true
    } else {
        todos[checkTodoId].completed = false
    }
```  
See how simple my teacher made the conditional statement.  
  
A. Teacher's code (He used 'find' method)
```JavaScript
    const todoToCheck = todos.find(function (todo) {
        return todo.id === id
    })
    if(todoToCheck !== undefined) {
        todoToCheck.completed = !todoToCheck.completed
    }
```
---

B. My code (I used if statement **to give true if the result is true lol**)

```JavaScript
   checkboxEl.setAttribute('type', 'checkbox')
   if (eachTodo.completed === true) {
       checkboxEl.setAttribute('checked', true)
   }
```

B. Teacher's code (He used the fact that **they both return boolean values** )

```JavaScript
   checkboxEl.setAttribute('type', 'checkbox')    
   checkboxEl.checked = eachTodo.completed
```

&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 11 Nov 2018 - Day 14

### JavaScript - with [freeCodeCamp](https://learn.freecodecamp.org/)

- Learned : Basics of JS - comparison - loop - accessing properties of object - array - random number
 
- Started : to keep track of what I want to recall, I started to make 'self-quiz' notes following FCC.
![screen shot 2018-11-13 at 12 44 31 pm](https://user-images.githubusercontent.com/42050917/48389677-fbe85d00-e741-11e8-83bc-4ae44ba2f0d6.JPG)
  

&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 9 Nov 2018 - Day 13

### JavaScript - Coded 'To-do app' along with Udemy JS course

- Learned : 
  localStorage methods (CRUD) and how to fetch the data into my JS code.  
  .setItem(), .getItem(), removeItem(), JSON.stringify(), JSON.parse()
    

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------  
## 8 Nov 2018 - Day 12

### JavaScript - Analyzed 'To-do app' logic. My solution vs. Teacher's solution

- Learned : 
  How to combine two similar functions into one, making code clean.  
  esp, the power of **logical operation in a single filter**, when two kinds of criteria are applied for filtering.  
  
  
### Today's coder shot
![code-recipes](https://user-images.githubusercontent.com/42050917/48263988-51cfb300-e46b-11e8-855f-25e4de3031b3.jpg)
![kakaotalk_photo_2018-11-09-14-28-46](https://user-images.githubusercontent.com/42050917/48263990-51cfb300-e46b-11e8-8fae-91533653febf.jpeg)


&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------  
## 7 Nov 2018 - Day 11

### JavaScript - Coded 'To-do app' along with Udemy JS course

- Learned : 
  How to code to-do logic (live-search, adding new items, starting off in clean slate)  
  
- Started :
  Asking questions in the course Q&A section and trying to think about others' questions, finding answers together (for the contents of the lectures I've already passed. Good job, Wonmi! 

### Solved Challenge 01
**Mission** : Deleting filtered items(elements that have the same value).  
**Solution** : Used _forEach_ instead of _.filter_ (5 Nov 2018)
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

### Solved Challenge 02
**Mission** Sorting the array in an alphabetical order, which has been sorted by boolean.. (6 Nov 2018)  
**Solution** : Used if statement to make two criteria of sort method.
```JavaScript
const sortTodos = function(todos) {
    const sortedList = todos.sort(function (todo1, todo2) {
        if(todo1.completed !== todo2.completed) {
            if (Number(todo1.completed) > Number(todo2.completed)) {
                return 1
            } else if (Number(todo1.completed) < Number(todo2.completed)) {
                return -1
            } else {
                return 0
            }
        } else {
            if (todo1.text.toLowerCase() > todo2.text.toLowerCase()) {
                return 1
            } else if (todo1.text.toLowerCase() > todo2.text.toLowerCase()) {
                return -1
            } else {
                return 0
            } 
        }
    })
    return sortedList
}
console.log(sortTodos(todos))
``` 


&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------  
## 6 Nov 2018 - Day 10

JavaScript - Coded 'Expense Tracker' along with Udemy JS course

:new: Started [freeCodeCamp JavaScript course](https://learn.freecodecamp.org/)! 
Such a nice learning resource!

- Learned : use case of querySelector, addEventListener, good use of 'target'
- Self-Challage 02 : how to sort the array in an alphabetical order, which has been sorted by boolean. :round_pushpin:[solved](#Solved-Challenge-02).

### Best error of today 
```JavaScript
const body = document.querySelector('body')
const button = document.querySelector('button')

button.addEventListener('click', function (e) {
    e.textContent = 'hahaha'
})
```
&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 5 Nov 2018 - Day 9

JavaScript - messed around with methods, did related exercies

- Learned : Array seaching - indexOf(), .find(), .findIndex(), .filter()
- Self-Challage 01 unsolved : deleting filtered items from array :round_pushpin:[solved](#Solved-Challenge-01).

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 4 Nov 2018 - Day 8

JavaScript - 

- Learned : Object reference, string/number methods, 
			array methods to manipulate items
		    restaurant seat checker, number guessing game

- I really like this JS logic world. :D

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 3 Nov 2018 - Day 7

JavaScript - 

- Learned : object, object as an argument of function, 
			function returning an object,

- It's ok not to understand it at once. It's ok. Keep calm and just try it again.

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 2 Nov 2018 - Day 6

JavaScript - variable scope, return, object in function, access to property

- Built [To-do list](https://codepen.io/wonma/pen/jegdPW)(2nd) with cleaner code.

- Built [Gradient Generator](https://wonma.github.io/Background-generator)

- Feeling more and more used to making mistakes and finding solutions.

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 1 Nov 2018 - Day 5

JavaScript DOM manipulation - selectors / events / callback functions

- Rebuilt mini facebook again. (Rebuilding till I feel comfortable!)

- Built [To-do list](https://codepen.io/wonma/pen/jegdPW) (Yay! Finally!!.. but need to go over it till I get it firmly.)

- var JavaScript.attribute = "magical";

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 31 Oct 2018 - Day 4

Reviewed and finished exercises of Javascript Basics

- Learned [falsy values](https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a)

- Enjoyed coding [console version of mini facebook](https://codepen.io/wonma/pen/LgwPdv) while practicing flexbox.

- Learned the importance of of varible scope from my code error!
  [local vs. global variable](https://www.quora.com/What-happens-when-you-don%E2%80%99t-declare-a-variable-in-Javascript)

- Let's keep calm and practice again. :P

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 30 Oct 2018 - Day 3

Finished analyzing the usage of Flexbox in the layout of the sample website.
- Flexbox has power in aligning items in one line.
- It's pretty much controlling how to manipulate the available space.
- Useful for responsive layout. 

Learned basic strategies about SEO(meta description, backlink), Image Optimization.

Resumed Andre's Javascript course.
- Created [robot movement](https://codepen.io/wonma/pen/XxLNxo).

&nbsp;
&nbsp;
&nbsp;

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

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 28 Oct 18 - Day 1

Working on [Sample Travel Site](https://github.com/wonma/travel-site) from this great Udemy course, [Git a Web Developer Job](https://www.udemy.com/git-a-web-developer-job-mastering-the-modern-workflow/) by Brad Schiff.

Succesfully Finished deploying [the Travel Site](https://wonma.github.io/travel-site/) following the course! 

