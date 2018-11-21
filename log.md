# Learning log

|Date | since 28 Oct 2018 |
|:---:|:---------------------------------------|
|Content|Learnt, thoughts, progress, ideas, links|

----------------------------------------------------------  
## 21 Nov 2018 - Day 22

### Basic Javascript section in fCC  
from _'Find the Length of a String'_ to _'Iterate Through an Array with a For Loop'_  
:speech_balloon: I felt it is so important to get comfortable with creating common basic logic.  
  
:small_orange_diamond: upgraded my understanding of ...
- 'return' in functions  
_[Functions that return a function(stackoverflow)](https://stackoverflow.com/questions/7629891/functions-that-return-a-function)_
- array manipulation
- accessing object properties with bracket notation  

&nbsp;  

### Best Error of Today :sweat_drops:

Omg.. I thought I know what 'return' is but wow..  
**Remember if the method(function) you are using returns anything or not!!!! **. 
  
```JavaScript
// Let's make a queue!
function nextInLine(arr, item) {
  // 1st (failed)
  var newArr = arr.push(item);
  return newArr.shift();     // error says newArr.shift() is not a function
  
  // 2nd (failed)
  arr = arr.push(item);
  return arr.shift();     // error still says arr.shift() is not a function
  
  // last (succeeded)
  arr.push(item);     // The problem was in using push method. '.push(..)' doesn't return anything!!!!
  return arr.shift();
}

// Test
var testArr = [1,2,3,4,5];
console.log(nextInLine(testArr, 8));
``` 
_The function above is to make a queue. In Computer Science a queue is an abstract Data Structure where items are kept in order. New items can be added at the back of the queue and old items are taken off from the front of the queue._

&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 20 Nov 2018 - Day 21

### Object-oriented programming in FCC + set up hangman logic

:small_orange_diamond: Finished object-oriented programming section in FCC  
- Finished setting up basic 'Hangman game' logic
- Used a set of prototype methods for the instance of Hangman
- need to rebuild this over and over till the process feels comfortable! Practice makes perfect!

&nbsp;  

### Today's coder shot :camera:
Proud that I made it though with my own logic though it's not the most concise solution!
![hangman1](https://user-images.githubusercontent.com/42050917/48778727-502ea680-ed19-11e8-832a-2a87389492d5.gif)

&nbsp;  

### Best Error of Today :sweat_drops:

**Closure** doesn't mean it shouldn't take 'this' keyword for the name of method!

```JavaScript
function Bird() {
  let weight = 15;
  function getWeight() {
    return weight;
  }
}

const eagle = new Bird()

console.log(eagle.getWeight())
``` 
Should've been like below.
```JavaScript
function Bird() {
  let weight = 15;
  this.getWeight = function() {
    return weight;	// publicly available method that a bird object can use
  }
}

const eagle = new Bird()

console.log(eagle.getWeight())
```  

&nbsp;  
### My Code :ok_hand: vs. Better Code :thumbsup:

**A1. My code** (I set up a callback function)
```JavaScript
Hangman.prototype.getLetter = function (letterInput) {
    if (!this.guessedLetters.includes(letterInput)) {
        this.guessedLetters.push(letterInput)
        this.decrementNum(letterInput)       // call decrementNum function
    } else {
        alert('You already typed ' + letterInput)
    }
}

Hangman.prototype.decrementNum = function (letterInput) {  // separate decrementNum function
    if(!this.word.includes(letterInput)) {
        this.guessNum -= 1
    }
}
```  
Let's keep in mind that a conditional expression can be assigned to a variable.  
  
**A2. Teacher's code** (He made two if-statements)
```JavaScript
Hangman.prototype.getLetter = function (letterInput) {
    letterInput = letterInput.toLowerCase()	// chnage input to lowercase

    const isNewLetter = !this.guessedLetters.includes(letterInput)
    const isNoMatch = !this.word.includes(letterInput)

    if (isNewLetter) {
        this.guessedLetters.push(letterInput)
    } else {
        alert('You already typed ' + letterInput)
    }

    if (isNewLetter && isNoMatch) {	// test two criteria at once
        this.guessNum--
    }
}
```

&nbsp;  

**B1. My code** (I set up two criteria, didn't use an array method.)
```JavaScript
Hangman.prototype.checkStatus = function (){
    const remainingGuesses = this.guessNum > 0
    const allMatched = this.getPuzzle() === this.word.join()

    if(remainingGuesses && allMatched) {
        this.status = 'success'
    } else if(remainingGuesses && !allMatched) { 
        this.status = 'playing'
    } else {  
        this.status = 'fail' 
    }
}

```  
I could use different kinds of array methods!  
Using an 'every' method was the most concise solution.

**B2. Teacher's code** (3 solutions : forEach / filter / every)
```JavaScript
Hangman.prototype.calculateStatus = function () {
    // using forEach
    let finished = true
    this.word.forEach((letter)=>{
    	if(this.guessedLetter.includes(letter)) {
	} else {finished = false}  //if just a single letter doesn't have a match, this results in 'finished = false'
    })

    // below stays the same.
    if (this.remainingGuesses === 0) {
        this.status = 'failed'
    } else if (finished) {
        this.status = 'finished'
    } else {
        this.status = 'playing'
    }
}
```   
```JavaScript
Hangman.prototype.calculateStatus = function () {
    // using filter
    const lettersUnguessed = this.word.filter((letter) => {
    	return !this.guessedLetters.includes(letter)
    })
    const finished = lettersUnguessed === 0  // it results in 'finished =  true' when there's no unguessed letters.
}
```  
```JavaScript
Hangman.prototype.calculateStatus = function () {
    // using every
    const finished = this.word.every((letter) => this.guessedLetters.includes(letter)) // all array items have to be true for the method to return 'true' at the end.
}
```  
&nbsp;  

**C1. My code** (I assigned a value at each block.)
```JavaScript
// hangman.js
Hangman.prototype.showMessage = function () {
    if (this.status === 'playing') {
        guessNumEl.textContent = `Guesses left : ${firstQuiz.guessNum}`
    } else if (this.status === 'success') {
        guessNumEl.textContent = 'Greate work! You guessed the word.'
    } else {
        guessNumEl.textContent = `Nice try! The word was ${this.word.join('')}`
    }
}

// app.js
const showResult = function (firstQuiz) {
    puzzleEl.textContent = firstQuiz.getPuzzle()
    firstQuiz.showMessage()
}
```  
I have a tendency of not using _return_ in a function/method. Let's change this logic habit!
  
**C2. Teacher's code** (He used the advantage of returning value from a method)
```JavaScript
// hangman.js
Hangman.prototype.showMessage = function () {
    if (this.status === 'playing') {
        return `Guesses left : ${firstQuiz.guessNum}`
    } else if (this.status === 'success') {
        return 'Greate work! You guessed the word.'
    } else {
        return `Nice try! The word was ${this.word.join('')}`
    }
}

// app.js
const showResult = function (firstQuiz) {
    puzzleEl.textContent = firstQuiz.getPuzzle()
    guessNumEl.textContent = firstQuiz.showMessage()  // returned value goes here.
}
```  
&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 19 Nov 2018 - Day 20

### Object-oriented programming in FCC

:small_orange_diamond: Understood what prototype is!
- Prototype is considered with constructors (type blueprints).  
- A constructor can inherit prototype from higher level of constructor.  
- Objects refer to methods in its parent's prototype.  
- Cloning(copying) and just having access are totally different.  
- Inheritance happens when there is cloning!

&nbsp;  

### Best Error of Today :sweat_drops:

I shouldn't forget **to reset counstructor property** .
```JavaScript
function Animal() { }
Animal.prototype.eat = function() { console.log("nom nom nom"); };

function Dog() { }

Dog.prototype = Object.create(Animal.prototype)
Dog.prototype.bark = function () {
    console.log('Woof!');
}
// should've reset constructor property of Dog.prototype

let beagle = new Dog();

beagle.eat(); // Should print "nom nom nom"
beagle.bark(); // Should print "Woof!"
``` 
Dog.prototype inherited Animal.prototype.constructor too. I should have **reset constructor property**!  
Add : _Dog.prototype.constructor = Dog_  
&nbsp;
&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  

## 17, 18 Nov 2018 
- Couldn't do much for personal affairs.
- Looked through FCC, JS object-oriented programming section.
&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 16 Nov 2018 - Day 19

### JavaScript + HTML/CSS review

:small_orange_diamond: Hangman logic basic setup
- figured out errors in my logic for hangman
- failed to understand new concepts 'primitive and prototypical inheritance'  
  so couldn't move forward. Decided to hit object-oriented programming part in [FFC](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/object-oriented-programming) first.  

- reviewed file/folder architecture and dev setting(gulp, npm)
- what to use? SASS vs. postCSS (I think I'll use postCSS)
- found out difference between browsersync and live-server  
- [good article about gulp for beginners](https://coder-coder.com/gulp-tutorial-beginners/)

&nbsp;  

### Best Error of Today :sweat_drops:

**concatination** matters a LOT in functions.  
```JavaScript
Hangman.prototype.getPuzzle = function () {
    const output = this.word.forEach((letter) => {
        if (this.guessedLetters.includes(letter)) {
            return letter
        } else {
            return '*'}
        })
    return output
}

const firstQuiz = new Hangman('cat', 3)
const secondQuiz = new Hangman('cocacola', 3)

console.log(firstQuiz.getPuzzle())
console.log(secondQuiz.getPuzzle())
``` 
1st error:  
I didn't consider blank in the word.   
2nd error:    
I didn't make concatination logic for each letter. The code above just results in undefined. 
  
**Answer**
```JavaScript
Hangman.prototype.getPuzzle = function () {
    // this.guessedLetters.push(guessedLetter)
    let output = ''

    this.word.forEach((letter) => {
        if (this.guessedLetters.includes(letter)|| letter === ' ') {
            return output = output + letter   
        } else {
            return output = output + '*'
        }
    })
    
    return output
}
``` 

&nbsp;
&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 15 Nov 2018 - Day 18

### JavaScript

:small_orange_diamond: Object-oriented programming
- catching and throwing errors, 'use strict' declaration
- object-oriented programming
- constructor function and new instances (instance == unique object)
- prototype object  
:bulb:_"The whole point of the constructor function is to set up that unique object and then get access to it.”_
:bulb:_"Constructor functions allow us to customize the individual instances."_

&nbsp;  

### Best Error of Today :sweat_drops:

**'return' WHERE** matters a LOT in functions.  
```JavaScript
Person.prototype.introduceLikes = function () {
    let introduceWhole = `Hi, my name is ${this.firstName}`
    this.likes.forEach((like)=>{
       return introduceWhole += `I love ${like}.`
    })
}
console.log(me.introduceLikes())
}
``` 
This crashes 'cuz the method _'introduceLikes'_ doesn't return anyting, but resulting in '**undefined**'.   
By mistake, I put 'return' inside of forEach callback function, and that was all.  
Woops, I'll probably dream of 'return' tonight.
 
&nbsp;  

### Today's coder shot :camera:
I was impressed with the concept of object-oriented programming.
![screen shot 2018-11-15 at 7 44 56 pm](https://user-images.githubusercontent.com/42050917/48547906-04da5980-e90f-11e8-9eab-24a744814c4f.JPG)
_by Teacher Andrew Mead, Udemy[the Modern JavaScript Bootcamp 2018](https://www.udemy.com/modern-javascript/)_

&nbsp;
&nbsp;
&nbsp;
&nbsp;  




----------------------------------------------------------  
## 14 Nov 2018 - Day 17

### JavaScript
on building notes-app & todos-app  

:small_orange_diamond: Arrow function - Ternary operator - Truthy/falsy values - Type coercion

&nbsp;  

### Best Error of Today :sweat_drops:

**'return'** matters a LOT in functions.  
Reviewed : function declaration, function expression (in an anonymous function), concept of 'returning' a value  

```JavaScript
const getData = () => {
    const todosJSON = localStorage.getItem('todos')
    todosJSON ? JSON.parse(todosJSON) : []
}
``` 
This crashes 'cuz it getData doesn't return anyting, but just resulting in '**undefined**' .
I should've put 'return' before the ternary operator.  
Then, it returns a type of array, not undefined.
 
### Today's coder shot :camera:  

![screen shot 2018-11-14 at 9 15 14 pm](https://user-images.githubusercontent.com/42050917/48481898-6dafcc00-e852-11e8-9591-d55a1f7f900f.JPG)
_Todos-app(left), Notes-app(right)_

&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 13 Nov 2018 - Day 16

### JavaScript

:small_orange_diamond: continued building notes-app & todos-app.  
	    Syncing data across pages / JS date () / moment js /  
	    integrating dates into the app (sort by recency or last edition)
 
### My Code :ok_hand: vs. Better Code :thumbsup:

A1. My code  
(I could've accessed the individual note's timestamp in note-edit.js .)
```JavaScript
// note-functions.js  
const generateLastEdited = (note) => {
    const lastTimestamp = note.updatedAt
    timeInfo.textContent = `Last edited ${moment(lastTimestamp).fromNow()}`
}
```  
Tearcher did 'real' refactoring. He separted a function and just let it return a value.  
Then, used the value where he needs it. 
  
A2. Teacher's code (He simply got the timestamp passed into a function.)
```JavaScript  
// note-functions.js  
const generateLastEdited = (timestamp) => `Last edited ${moment(timestamp).fromNow()}` 
  
// note-edit.js
timeInfo.textContent = generateLastEdited(matchedNote.updatedAt)
```  

&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 12 Nov 2018 - Day 15

### JavaScript

:small_orange_diamond: continued building notes-app & todos-app.  
	    improved the features with id(using uuid) / location.assign / complex DOM structure
 
### My Code :ok_hand: vs. Better Code :thumbsup:

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

:small_orange_diamond: Basics of JS - comparison - loop - accessing properties of object - array - random number
 
:new:  Started to keep track of what I want to recall, I started to make 'self-quiz' notes following FCC.
![screen shot 2018-11-13 at 12 44 31 pm](https://user-images.githubusercontent.com/42050917/48389677-fbe85d00-e741-11e8-83bc-4ae44ba2f0d6.JPG)
  

&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 9 Nov 2018 - Day 13

### JavaScript - Coded 'To-do app' along with Udemy JS course

:small_orange_diamond: localStorage methods (CRUD) and how to fetch the data into my JS code.  
  .setItem(), .getItem(), removeItem(), JSON.stringify(), JSON.parse()
    

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------  
## 8 Nov 2018 - Day 12

### JavaScript - Analyzed 'To-do app' logic. My solution vs. Teacher's solution

:small_orange_diamond: How to combine two similar functions into one, making code clean.  
  esp, the power of **logical operation in a single filter**, when two kinds of criteria are applied for filtering.  
  
  
### Today's coder shot  :camera:
![code-recipes](https://user-images.githubusercontent.com/42050917/48263988-51cfb300-e46b-11e8-855f-25e4de3031b3.jpg)
![kakaotalk_photo_2018-11-09-14-28-46](https://user-images.githubusercontent.com/42050917/48263990-51cfb300-e46b-11e8-8fae-91533653febf.jpeg)


&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------  
## 7 Nov 2018 - Day 11

### JavaScript - Coded 'To-do app' along with Udemy JS course

:small_orange_diamond: How to code to-do logic (live-search, adding new items, starting off in clean slate)  
  
:new: Started asking questions in the course Q&A section and trying to think about others' questions, finding answers together (for the contents of the lectures I've already passed. Good job, Wonmi! 

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

:small_orange_diamond: JavaScript - Coded 'Expense Tracker' along with Udemy JS course

:new: Started [freeCodeCamp JavaScript course](https://learn.freecodecamp.org/)! 
Such a nice learning resource!

- querySelector, addEventListener, good use of 'target'
- Self-Challage 02 : how to sort the array in an alphabetical order, which has been sorted by boolean. :round_pushpin:[solved](#Solved-Challenge-02).

### Best error of today :sweat_drops:
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

:small_orange_diamond: JavaScript - messed around with array methods, did related exercies

- Array seaching - indexOf(), .find(), .findIndex(), .filter()
- Self-Challage 01 unsolved : deleting filtered items from array :round_pushpin:[solved](#Solved-Challenge-01).

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 4 Nov 2018 - Day 8

:small_orange_diamond: JavaScript   

- new : Object reference, string/number methods, 
	array methods to manipulate items
	restaurant seat checker, number guessing game

:speech_balloon: I really like this JS logic world. :D

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 3 Nov 2018 - Day 7

:small_orange_diamond: JavaScript

- new : object, object as an argument of function,  
	function returning an object,

:speech_balloon: It's ok not to understand it at once. It's ok. Keep calm and just try it again.

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 2 Nov 2018 - Day 6

:small_orange_diamond: JavaScript - variable scope, return, object in function, access to property

- Built [To-do list](https://codepen.io/wonma/pen/jegdPW)(2nd) with cleaner code.

- Built [Gradient Generator](https://wonma.github.io/Background-generator)

- Feeling more and more used to making mistakes and finding solutions.

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 1 Nov 2018 - Day 5

:small_orange_diamond: JavaScript DOM manipulation - selectors / events / callback functions

- Rebuilt mini facebook again. (Rebuilding till I feel comfortable!)

- Built [To-do list](https://codepen.io/wonma/pen/jegdPW) (Yay! Finally!!.. but need to go over it till I get it firmly.)

- var JavaScript.attribute = "magical";

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 31 Oct 2018 - Day 4

:small_orange_diamond: Reviewed and finished exercises of Javascript Basics

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

:small_orange_diamond: Finished analyzing the usage of Flexbox in the layout of the sample website.
- Flexbox has power in aligning items in one line.
- It's pretty much controlling how to manipulate the available space.
- Useful for responsive layout. 

:small_orange_diamond: Learned basic strategies about SEO(meta description, backlink), Image Optimization.

:small_orange_diamond: Resumed Andre's Javascript course.
- Created [robot movement](https://codepen.io/wonma/pen/XxLNxo).

&nbsp;
&nbsp;
&nbsp;

----------------------------------------------------------
## 29 Oct 18 - Day 2

:small_orange_diamond: Reviewed command line basics.
- Figured out (AGAIN) the importance of distinguishing between relative paths and absolute paths.
- Understood what is home directory and root directory in perspective of terminal.

:small_orange_diamond: Set up browserSync package from scratch.
- Made it possible to watch multiple html docs (with separate tasks).
- Set up a basic startup working file.

:small_orange_diamond: Played with Flexbox.
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

