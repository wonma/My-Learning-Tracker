# Learning log

|Date | since 28 Oct 2018 |
|:---:|:---------------------------------------|
|Content|Learnt, thoughts, progress, ideas, links|

----------------------------------------------------------  
## 20 Dec 2018 - Day 39   

### [Andre's JS course on Udemy](https://www.udemy.com/the-complete-web-developer-zero-to-mastery/) 

&nbsp;
:small_orange_diamond: Started to learned React about...      
- Starting with 'create-react-app' package
- basic JSX syntax for DOM
- Component & 'props'
- random image API : https://robohash.org

### Best Error of Today :sweat_drops:

**How to get into JS mode in JSX**. 
  
```JavaScript 
// Wrong
const Card = (props) => {
	return (
		<div className="bg-light-green dib br3 pa3 ma2 grow bw2 shadow-5">
			<img src=`https://robohash.org/{props.id}?200x200` alt="robot1" />  // Error occurs here
			<h1>{props.name}</h1>
			<p>{props.email}</p>
		</div>
	)
}
```  
_Curly brackets are not the operators for getting into JS mode! it's part of JSX syntax_  

```JavaScript 
// Fixed
const Card = (props) => {
	return (
		<div className="bg-light-green dib br3 pa3 ma2 grow bw2 shadow-5">
			<img src={`https://robohash.org/${props.id}?200x200`} alt="robot1" /> // Fixed here
			<h1>{props.name}</h1>
			<p>{props.email}</p>
		</div>
	)
}
```  

### My Question Was.. :question:
**Can't I just use 'map' to loop over 10 robot data in 'index.js' ?**  
**Why do I have to create 'Cardlist.js', which is one more additional JS file?**
(will think more on this tomorrow)

### Today's coder shot :camera:
I finally started to build with React! 
![screen shot 2018-12-21 at 12 28 13 am](https://user-images.githubusercontent.com/42050917/50293731-96615c00-04b7-11e9-82b1-a461e6cbc18e.JPG)


&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 19 Dec 2018 - Day 38   

### [Andre's JS course on Udemy](https://www.udemy.com/the-complete-web-developer-zero-to-mastery/) + Recipe App

&nbsp;
:small_orange_diamond: Learned about...      
- How to contribute to open source  
- Fork & clone repo on Github  
- Branch, merge conflict, PR(pull request)  
- Typical day of developer (git checkout master, git pull... / Trello)   

&nbsp;  
:small_orange_diamond: For Recipe-app...      
- Fixed a bug (type not getting saved)   
- Added 'add other ingredient' feature on index.html   
- Fixed 'match score' calculation logic   
- Fixed filter so it can check a word included in a phrase too (ex. 'pork' in 'pork loin')
- Implemented 'delete' button on edit.html   

&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 17 Dec 2018 - Day 37   

### [Andre's JS course on Udemy](https://www.udemy.com/the-complete-web-developer-zero-to-mastery/)

&nbsp;
:small_orange_diamond: Reviewed and did exerciese for...    
- ES8 features: Object.values(obj), Object.entries(obj)  
- loops, for of, for in loop (iterable-> string, array vs. emunarable->obj)  
- How JavaScript Works (synchronous, asynchronous)  
  (taking an example of Web API's setTimeout function, setting time at '2000' or '0' milliseconds)
- Need to learn more later about JS run-time environment (Web API, callback queue, event loop)

&nbsp;  
### _"Javascript as a single threaded language that can be non-blocking."_    
&nbsp;    
### My Code :ok_hand: vs. Better Code :thumbsup: 
```JavaScript  
// Mission : creating a function that returns the biggest number in an array
const array = [-1, 0, 3, 100, 99, 2, 99] // should return 100
const array2 = ['a', 3, 4, 2] // should return 4
const array3 = [] // should return 0
```  

**A1. My code** (used 'reduce')

```JavaScript
function biggestNumberInArray(arr) {
    return arr.reduce((acc, each)=>{ return acc < each ? each : acc }, 0)
}
```   
  
**A2. Teacher's code** (used 'for')
```JavaScript
function biggestNumberInArray(arr) {
  let highest = 0;
  for (let i = 0; i < arr.length; i++) {
    if (highest < arr[i]) {
      highest = arr[i];
    }
  }
  return highest
}
```
  
&nbsp;
&nbsp;
&nbsp;  
&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 16 Dec 2018 - Day 36   

### Buliding Recipe App  (D4)

&nbsp; 
:small_orange_diamond: Completed 'Edit' page   
- Linking values of ingredient inputs to each property on localStorage
- Enabling 'remove' ingredient function, fixing 'add' ingredient functionality
- Initiating 'edit page' with DOM generating functions


&nbsp;  
![screen shot 2018-12-16 at 6 25 42 pm](https://user-images.githubusercontent.com/42050917/50052047-1490cc00-0161-11e9-9231-ea32ebc8736a.JPG)


&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 14 Dec 2018 - Day 35   

### Buliding Recipe App (D3)

&nbsp;
:small_orange_diamond: Added functionality of ...    
- Saving and fetching data from localStorage
- Saving button for the whole form values
- Adding ingredient input boxes with plus button

&nbsp;  
### Errors & Solution  
**A. JSON, who's assigning 'null'..**  
(didn't know why I kept getting 'null' for recipes. 
I was like, "what's wrong? recipes is just empty array not a null!"  
But the fact was that JSON was reassigning 'null' to recipes.)  
```JavaScript
let recipes = []

const getData = () => {
    recipes = JSON.parse(localStorage.getItem('recipes'))
    return recipes
}
```   
  
**Fixed** 
```JavaScript
let recipes = []

const loadData = () => {
    const recipesFromJSON = localStorage.getItem('recipes')
    
    try {
        return recipesFromJSON ? JSON.parse(recipesFromJSON) : []
    } catch (e) {
        return []
    }
}

recipes = loadData()

const getData = () => recipes
```

**B. When you want a specific 'object' out of array..**  
(Even though it's just 'one' thing out of array, if the thing is 'object' 
I must use 'find', not 'filter'...!!!
Because filter always returns an array!)    
```JavaScript
const theRecipe = recipes.filter((recipe) => recipe.id === recipeID)
// theRecipe logs out '[{...}]'
// typeof theRecipe is 'array'
```   
  
**Fixed** 
```JavaScript
const theRecipe = recipes.find((recipe) => recipe.id === recipeID)
// theRecipe logs out '{id:.., title:...}'
// typeof theRecipe is 'object'
```
&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 13 Dec 2018 - Day 34   

### Resumed [Andre's JS course on Udemy](https://www.udemy.com/the-complete-web-developer-zero-to-mastery/)

&nbsp;
:small_orange_diamond: Learned advanced JS topics of ...    
- Useful 'returing' array methods, '.map(), filter(), .reduce()'  
- Creating a class using 'Class', 'extends', 'super'  
- ES7 features: includes(), exponential operator 지수 연산자  
- ES8 features: str.padStart(10, '='), str.padEnd(10), Object.values(obj), Object.entries(obj)  
- for of, for in loop (iterable-> string, array vs. emunarable->obj)  
- How JavaScript Works (synchronous, asynchronous)
- V8 engine's memery heap & call stack
- JavaScript runtime environment (Web API, callback queue, event loop)
- Modules (+ why it's needed)  
&nbsp;  
### _"Javascript as a single threaded language that can be non-blocking."_  
![screen shot 2018-12-14 at 1 37 44 am](https://user-images.githubusercontent.com/42050917/49953197-ed5bb400-ff40-11e8-99f1-a717ee57fcbd.JPG)  
_From [Andre's JS course on Udemy](https://www.udemy.com/the-complete-web-developer-zero-to-mastery/)_  
&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 12 Dec 2018 - Day 33   

### Buliding Recipe App  (D2)

&nbsp;
:small_orange_diamond: Features (added)   
- Sorting by 'matching rate' (activated when an ingredient is checked)
- Links to 'Edit' or 'View' page
- Edit page DOM manipulation (working on)  
&nbsp;  
![haha](https://user-images.githubusercontent.com/42050917/49872942-ead45e00-fe5d-11e8-91f7-20b17087a816.jpg)


&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 11 Dec 2018 - Day 32   

### Started building Recipe App  (D1)
Good practice to make the learned skills my own!
![screen shot 2018-12-12 at 2 47 55 am](https://user-images.githubusercontent.com/42050917/49819294-624fb200-fdb8-11e8-90c8-4d65bf250fe1.JPG)

&nbsp;
:small_orange_diamond: Features (so far)   
- Ingredient checkbox filtering
- Food type radio button filtering
- Evaluating the score of recommended recipes

  
&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 10 Dec 2018 - Day 31   

### Completed my first JS Bootcamp course!
:tada: Completed Modern JavaScript Bootcamp course on Udemy!
![screen shot 2018-12-12 at 2 27 53 am](https://user-images.githubusercontent.com/42050917/49818307-b9a05300-fdb5-11e8-9995-c5cfa537c91a.JPG)


&nbsp;
:small_orange_diamond: learned advanced JS features such as ..    
- Rest Parameter '...parameterName' eg) calculateAverage
  (I can put arguments in functions as much as I want! It automatically creates an array out of the arguments)  
- Spread Syntax (copy, update array)
- Object Spread Syntax (object merging)
- Destructuring (creating new constant variables, fetched from a specific object, with default value and customized local variable name)

### My Code :ok_hand: vs. Better Code :thumbsup:   
**A1. My code** (couldn't come up with join method)
```JavaScript
const printTeam = (teamName, coach, ...players) => {
    let teamAll = ''
    players.forEach((player) => {
        teamAll += `, ${player}`
    })
    console.log(`Team Name: ${teamName}`)
    console.log(`Coach: ${coach}`)
    console.log(`Team members: ${teamAll}`)
}
```   
  
**A2. Teacher's code** 
```JavaScript
const printTeam = (teamName, coach, ...players) => {
    console.log(`Team : ${teamName}`)
    console.log(`Coach : ${coach}`)
    console.log(`Players : ${players.join(', ')}`)
}
```
  
&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 3 Dec 2018 - Day 30   

### To-do app refactoring & finishing up features
:tada: Deployed first version of [To-do App](https://wonmi-todo.netlify.com/)!     

&nbsp;
:small_orange_diamond: finished up the todo app by adding ..    
- styles
- a plural text message
- validation for new to-do input (trim, length > 0)
- the html structure of each to-do was the cherry on the top!

### My Code :ok_hand: vs. Better Code :thumbsup:  
Adding a plural text   
**A1. My code** (Do not repeat yourself!!)
```JavaScript
const generateSummaryDOM = (incompleteTodos) => {
    const summary = document.createElement('h2')
    if (incompleteTodos.length === 1) {
        summary.textContent = `You have ${incompleteTodos.length} item to complete`
    } else if (incompleteTodos.length >= 1) {
        summary.textContent = `You have ${incompleteTodos.length} items to complete`
    }
    return summary
}
```   
  
**A2. Teacher's code** (He made a variable 'plural' returning 's' or empty string.)
```JavaScript
const generateSummaryDOM = (incompleteTodos) => {
    const summary = document.createElement('h2')
    const plural = incompleteTodos.length === 1 ? '' : 's'
    summary.textContent = `You have ${incompleteTodos.length} item${plural} to complete`
    return summary
}
```
- Figured out the difference of between the teacher's code structure and mine  
- The teacher uses 'validation' for any input from user / returned value from .find, .findIndex.. etc.
  This kind of setup is also advantageous for preventing the app from crashing with unexpected returned values.   
![comparison2](https://user-images.githubusercontent.com/42050917/49421945-3f7c3700-f7d5-11e8-9330-11a341a13286.jpg)
  
&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 2 Dec 2018 - Day 29  

### JavaScript with Andrew Mead
:tada: Deployed first version of [Note App](https://wonmi-note-app.netlify.com/)!     
![noteapp](https://user-images.githubusercontent.com/42050917/49344204-81af5680-f6b7-11e8-8138-facffe72f95e.gif)  

&nbsp;
:small_orange_diamond: finished up the note app by ..    
- Adding styles  
- Adding 'no notes show-up' feature when there's no note  
- Figuring out the difference of between the teacher's code structure and mine  
![comparison](https://user-images.githubusercontent.com/42050917/49344096-609a3600-f6b6-11e8-8990-39ac8da0ec3e.jpg)

&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 29 Nov 2018 - Day 28  

### JavaScript Bootcamp in Udemy with Andrew Mead
:speech_balloon: Decided to use gulp for HTML,CSS browser-sync, while using webpack seperately for now.  
  
:wrench: Fixed issues on [Hangman app](https://wonmi-hangman.netlify.com/)    
1) Disabled autocapitalize on input area  
2) Changed 'typed letter noticing popup' to a fading-in text so that I doesn't disconnect user interaction  
3) Added 'wrong letters' section for better engagement  
![hangman2](https://user-images.githubusercontent.com/42050917/49235377-53bedd80-f43d-11e8-8406-0f18d8d8763e.gif)  

:small_orange_diamond: met these new concepts of..  
- the power of Webpack  
  (JS module system / babel-loader, babel polyfill / minimize JS)   




&nbsp;
&nbsp;
&nbsp;  
 

----------------------------------------------------------  
## 28 Nov 2018 - Day 27

### JavaScript

:small_orange_diamond: JS bootcamp + fCC ES6
- Understanding Babel  
  (Babel allows us work in a wider range of browsers even if we’re using super modern JS features)
- Understand var, let, const (fCC)
- **Added a keypad activating feature to Hangman app.**  

```JavaScript
// Restrict the scope of i
function checkScope() {
"use strict";
  let i = "function scope";
  if (true) {
    let i = "block scope";
    console.log("Block scope i is: ", i);
  }
  console.log("Function scope i is: ", i);
  return i;
}
```
_the variable 'i' inside of if statement only affects 'i' inside of if statement._

&nbsp;
&nbsp;
&nbsp;  
 

----------------------------------------------------------  
## 26 Nov 2018 - Day 26

### JavaScript Bootcamp in Udemy
:speech_balloon: I got much closer to JavaScript. So glad that reading syntax is not that intimidating now. :D    
  
:tada: Finally deployed my first [Hangman app](https://wonmi-hangman.netlify.com/)!  
![hangman](https://user-images.githubusercontent.com/42050917/49035213-84153a80-f1f7-11e8-9ee9-a6795a5e0cd2.gif)
  

:small_orange_diamond: met these new concepts of..  
- Async function & await  
  (I liked how 'await' lets me be free from having to set up 'throw new error' from promises.)
- Hosting with Netlify
```JavaScript

const processData = async () => {  // resulting in 'promise'!!!
    let data = await trippleNum(data)   // await와 함께 promise만들 callback펑션 써줌
        data = await trippleNum(data)  // await는 똑똑해서 promise에서 reject되면 자동으로 throw error함.
    return data
}

processData().then((data) => {
    console.log('Data:', data)
}).catch((error) => {  // Promise에서 에러리포트할 경우에만 catch작동 
    console.log(error)
}) 
```
_Quick view on 'async & await'_

&nbsp;  

### Best Error of Today :sweat_drops:

**'undefined' could mean something has to be returned but didn't!**. 
  
```JavaScript
// Setting up 'async + await' 
const getCountryName = async (countryCode) => {
    const response = await fetch('//restcountries.eu/rest/v2/all', {})
    if (response.status === 200) {
        const countries = response.json()  // I missed 'await' here.
        return countries.find((country) => country.alpha2Code === countryCode)    
    } else {
        throw new Error('Unable to fetch data')
    }
}
```  
_'await' is like 'please, wait for this guy to be done!(to the following expressions)'_

&nbsp;
&nbsp;
&nbsp;  
  

----------------------------------------------------------  
## 24~25 Nov 2018 - Day 25

### JavaScript Bootcamp in Udemy
:speech_balloon: So glad that I can code everyday.

:small_orange_diamond: met these new concepts of..  
- Promise (resolve, rejcect)  
  : more intuitive way to construct asynchronous execution with built-in error handler 
(compared to callback formation)
- Promise chaining  
  : receiving data from the first execution and using it afterwards.
- Fetch API  
  : a different way to make HTTP request
  (compared to creating new instance of XMLHttpRequest( ) )

&nbsp;  

### Best Error of Today :sweat_drops:

**'undefined' could mean something has to be returned but didn't!**. 
  
```JavaScript
const getCountryName = (countryCode) => {
    return fetch('https://restcountries.eu/rest/v2/all', {}).then((response) => {
        if (response.status === 200) {
            return response.json()
        } else {
            throw new Error('Unable to fetch data')
        }
    }).then((countries) => {
        return countries.find((country) => {country.alpha2Code === countryCode})
			// 'find' method's anonymous function doesn't return anything!
    })
}
```  
_check return in functions more carefully!!!_

&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 23 Nov 2018 - Day 24

### Udemy JS bootcamp + FCC JS basic section (100% done)
:speech_balloon: The first meeting of new concepts are tough by nature. But the more I pay interest in it, the stronger weapon they will become eventually!

:small_orange_diamond: Studied ...  
- Asynchronous vs. synchronous
- Closure (lexical environment, private variable, currying - Tipper)
  [MDN explanation of closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures) was super helpful.
- Callback function to be able to use fetched data(from http request)

&nbsp;  

### Today's coder shot :camera:
I finally understood why callback matters in using fetched data. 
![callback_visual](https://user-images.githubusercontent.com/42050917/48982850-2d422f00-f12b-11e8-932b-c610d6fc9431.jpg)

_while using HTTP request in Udemy_

&nbsp;
&nbsp;
&nbsp;  

----------------------------------------------------------  
## 22 Nov 2018 - Day 23

### JavaScript Bootcamp in Udemy
:speech_balloon: Getting data from third-party servers is so interesting!  

:small_orange_diamond: upgraded hangman logic/code with...  
- 'Class' syntax
- messed around with subclasses
- HTTP request, JSON data 

&nbsp;  

### Best Error of Today :sweat_drops:

The order of when requests are done matters.
**You might have been trying to access data when it's still in loading.**. 
  
```JavaScript
// Let's find the name of country of code 'KR'
const request2 = new XMLHttpRequest()

let countries = []

request2.addEventListener('readystatechange', (e) => {
    if (e.target.readyState === 4 && e.target.status === 200) {
        countries = JSON.parse(e.target.responseText)       
    } else if (e.target.readyState === 4) {
        console.log('Error has been detected.')
    }
})

request2.open("GET", "https://restcountries.eu/rest/v2/all")
request2.send()

const country = countries.find((element) => element.alpha2Code === "KR")  // Even before JSON data get assigned to 'countries'
console.log(country.name) // can't access name property of 'undefined'
```  
right code below  
```JavaScript
const request2 = new XMLHttpRequest()

request2.addEventListener('readystatechange', (e) => {
    if (e.target.readyState === 4 && e.target.status === 200) {
        const countries = JSON.parse(e.target.responseText)  
        const country = countries.find((element) => element.alpha2Code === "KR") // The code got moved to here.
        console.log(country.name)
    } else if (e.target.readyState === 4) {
        console.log('Error has been detected.')
    }
})

request2.open("GET", "https://restcountries.eu/rest/v2/all")
request2.send()
```
_Check out why in the shot below!_
&nbsp;   

### Today's coder shot :camera:
I was accessing the data in 'app.js' even before the data(array) wasn't even parsed from 'all' yet..
![screen shot 2018-11-22 at 9 41 19 pm](https://user-images.githubusercontent.com/42050917/48903623-65cdd880-ee9f-11e8-82af-98bfaca632f8.JPG)

_Exploring HTTP request in Udemy_

&nbsp;
&nbsp;
&nbsp;  


----------------------------------------------------------  
## 21 Nov 2018 - Day 22

### Basic Javascript section in fCC  
80% done.    
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

### Today's coder shot :camera:
I was proud that I could figure it out by myself, applying some tip I learned from Andrew Mead.
![screen shot 2018-11-21 at 11 39 06 pm](https://user-images.githubusercontent.com/42050917/48848211-b9302000-ede6-11e8-9eba-1ff89a29ab3b.JPG)
_'Record Collection' challenge in FCC_

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

