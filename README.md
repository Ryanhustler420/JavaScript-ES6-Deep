# JavaScript-ES6-Deep

```javaScript

console.log("Hey Everyone");

```
> Var Scoping Refresher

``we have three ways to declare variable in javaScript``

```javaScript
var width = 100;
let height = 200;
const name = "base"
```

> var keyword was there is javaScript before es6

```benefits  of using var keyword is we can reassign them or update them```


```javaScript
// update them
var width = 200;
console.log(width); // 200

width = 400;
console.log(width); // 400

```

``or``

```javaScript

// we can put 'var' keyword in fornt of same variable name (Dont do this until require.)

var width = 200;
console.log(width); // 200

var width = 400;
console.log(width); // 400

```

> another thing we shold care about how variable are scoped

scoping meaning were are these variable are available to me and var variable are function scoped
which means that they are only available inside the function that there are created or they are not created inside a function at all
this var varible are global scope which is why they are avilable inside console of browser



```javaScript

function setWidth(){
  // this var is scoped local to this function so outside of this function cant access it.
  var width = 100;
  console.log(width);
}

setWidth(); // 100

console.log(width); // throw error

```
> to access the width varible we have to make that global and update that from function

```javaScript

var width = 100;
function setWidth(){
  // we are accessing this global width outside the function
  // and changing the original value
  width = 400;
  console.log(width);
}

setWidth(); // 400

console.log(width); // 400


```

> var variable are function scoped we can assess var from outside the block were they define.

```javaScript

var age = 100;
if(age > 12){
  // this is not a function that why the var dogYears is expose to outside assess.
  var dogYears = age * 7; // this var variable is local to the function scope.
  console.log(`you are ${dogYears} dog years old.`);
}

console.log(dogYears); 
// we can access the dogYears which is define inside if block because var is a function scope

```
**to solve the issue where you cant shere the temp variable is define inside a block to outside use let and const**

> example let keyword

```javaScript

var age = 100;
if(age > 12){
  // this is not a function that why the var dogYears is expose to outside assess.
  let dogYears = age * 7; // this var variable is local to the function scope.
  const name = 'puff';
  console.log(`you are ${dogYears} dog years old.`);
}

console.log(name); // ""
console.log(dogYears); // throw error ReferenceError: dogYears is not defined

```

>  these two are added in Es6 with some attribute with them

```javaScript

let height = 200;
const key = 'abc123';

```

## let vs const

**you cannot declare two let variable like var keyword**

```javaScript

let points = 50;
let points = 60;  //Uncaught SyntaxError: Identifier 'points' has already been declared

```

> but you can update them

```javaScript

let points = 50;
points = 60;

```

> we can declear same variable name inside block of code and that won't affect the code at all

```javaScript

let points = 50;
let winner = false;

if(points > 40){
  console.log("it ran");
  let winner = true; //inside a block wont affect outside scope variable but var can
}

console.log(winner);

//output
  // it ran1
  // false

```

## const variable cannot be updated but let variable can

```javaScript

const key = 'abc1230';

key = 'change'

// Uncaught TypeError: Assignment to constant variable.

```

> something poople think const is muteable

```javaScript

const person = {
  name:'wes',
  age:28
}

//try to update that

person = {name:"Gaurav"} //TypeError: Assignment to constant variable.

//NOTE: you cannot do that const variable is not meant for reassigning


```

**but a property of a const variable can change**

```javaScript

person.name = "Gaurav";
person.age = 20;

console.log(person); //{name: "Gaurav", age: 20}


```

>  but you can freeze object by using

```javaScript

const wes = Object.freeze(person);

wes.name = "saurav" // try to assign new value
console.log(wes); // {name: "Gaurav", age: 20}



```


## let and const is real world

> Replacement of IIFE help us not to leak information

```javaScript


var name = 'wes';

//it wont leak name property to global scope
(function(){
  var name = 'gaurav';
  console.log(name);
})();

console.log(name); //wes
//not gaurav because that's inside the IIFE block

```

## const is a block level variable

```javaScript

//since const is a block level scope of variable

{
  const name = "GauravGupta";
}

console.log(name); // ""

```

> another good example of let and const is for loop 

```javaScript

for (var i = 0; i < 10; i++) {
  console.log(i);
}

// output -> 1 2 3 4 5 6 7 8 9

// But we can still use var i

console.log(i); // 10

```
>  to solve this problem we can use let keyword in for loop

``Use Let Keyword in for loop``
```javaScript

for (let j = 0; j < 10; j++) {
  console.log(j);
}

//we cannot access let j because that inside the block of for loop

console.log(j); //ReferenceError: j is not defined

```

> var keyword example

```javaScript

//example var
for (var j = 0; j < 10; j++) {
  console.log(j);
  setTimeout(() =>{
      console.log(j); //10
  },2000);
}

```

> let keyword example

```javaScript

for (let j = 0; j < 10; j++) {
  console.log(j); // 0 1 2 3 4 5 6 7 8 9
  setTimeout(() =>{ // after 2 second
      console.log(j); // 0 1 2 3 4 5 6 7 8 9
  },2000);
}

```

## Temporal Dead Zone


```javaScript

var pizza = 'Deep Dish';
console.log(pizza);

// output : Deep Dish


```


```javaScript

console.log(pizza);
var pizza = 'Cool Dish';

// output : undefine
// because with var keyword we can access the variable before we declear it

```

> Simple fix use const keyword

```javaScript

console.log(hello);
const hello = 'Cool Dish';

// output :- ReferenceError: hello is not defined

```

##  Arrow Function

```javaScript

const names = ['wes','kait','lux'];

```

> Arrows is a new syntax for functions, which brings several benefits:

- Arrow syntax automatically binds this to the surrounding code’s context
- The syntax allows an implicit return when there is no body block, resulting in shorter and simpler code in some cases
- Last but not least, => is shorter and simpler than function, although stylistic issues are often subjective

```javaScript

//name function

const fullNames = names.map(function(name){
  return `${name} bos`;
});

console.log(fullNames);

```

``rewrite it as arrow function``
- explicit return where we write return keyword

```javaScript

const fullNames = names.map((name) => {
  return `${name} bos`;
});

console.log(fullNames);

// OR if you have only one args

const fullNames = names.map(name => {
  return `${name} bos`;
});

console.log(fullNames);


```

``more simpler``

- if you have one statement to return
- with Implicit return

```javaScript

const fullNames = names.map(name => `${name} bos`);

console.log(fullNames);

```

**ES6 arrow functions are anynoumos function meaning running without blocking other function execution**

```

Name functions
it help us for stack trace like if somthing went wrong so the logger
will let us know were the line number is.

```


```javaScript

function sayMyName(name){
  alear(`hello ${name}`)
}

sayMyName("Gaurav")


```
> if you using Arrow function you cannot name them at all but you can store them inside a variable name

``Example``


```javaScript

const sayMyName = (name) => {
  alert(`Hello ${name}`)
}

sayMyName("Hey gupta");

//NOTE: this wont give you stack trace be carefull

```

## lets look at couple of more example of Arrow function


> implicit return with object litral

```javaScript

const Race = '100m Dash';
const Winner = ['Hunter Gate','Singa Song','Imda Bos'];

const Win = Winner.map((Winner,i) => ({name:Winner,race:Race,place:i+1}));

console.table(Win);

```

> filtering array using arrow function

```javaScript

const ages = [23,62,45,234,2,65,324,654,12];

const old = ages.filter(age => age >= 60);

console.log(old);

```

## Default function arguments

```javaScript

function calculateBill(total,tax,tip){
    return total + (total * tax) + (total * tip);
}

// const totalBill = calculateBill(100); <--undefined
// const totalBill = calculateBill(100,0.13,0.15); <- you have to do this


```

``Simple Fix```

```javaScript

function calculateBill(total,tax = 0.13,tip = 0.15){
    return total + (total * tax) + (total * tip);
}

const totalBill = calculateBill(100,undefined,0.15); // pass

// here argument order does metter but as you will learn 
// object distructring than you can put args as any order as you want

```

## Why Not Use an Arrow Function

> When you need a method to bind to an object

```javaScript

const person = {
    points:23,
    score(){ // this is where you can bind properties of 
             // an object which cannot be achive by fat Arrow Function
        console.log(this);
        this.points++;
    }
}

console.log(person);
person.score();
person.score();
person.score();
person.score();
console.log(person);

```

- When you need to add a prototype method
- this is simply just the process of adding methods or properties to an object 
- after the object is created

```javaScript

class Car{
    constructor(make,colour){
        this.make = make;
        this.colour = color;
    }
}


const beemer = new Car('bmw','blue');
const alfa = new Car('alfa','white');


Car.prototype.summarize = () => {
    return `This car is a ${this.make} in the colour ${this.colour}`;
};

// this above method will give undefine output 


beemer.summarize()
// This car is a undefined in the colour undefined
// because this is fat arrow function

```
``simple fix``

```javaScript

// use simple function for binding this keyword with the current context

Car.prototype.summarize = function(){
    return `This car is a ${this.make} in the colour ${this.colour}`;
}

beemer.summarize();
// This car is a beemer in the colour blue

```
When you need arguments object 
arguments -> is a keyword in javaScript which can fetch args from function 
Eventhough you dont have formal args


```javaScript

const orderChildren = () => {
    const children = Array.from(arguments);
    return children.map((child,i) => {
        return `${child} was child #${i+1}`;
    })
    console.log(arguments); 
}

orderChildren('jill','gaurav','amit');
// this function will throw an error because of arrow function

```

``simple fix``

```javaScript

const orderChildren = function(){
    const children = Array.from(arguments);
    return children.map((child,i) => {
        return `${child} was child #${i+1}`;
    })
    console.log(arguments); 
}
orderChildren('jill','gaurav','amit');
// jill was child #1,gaurav was child #2,amit was child #3 

```

> more code available in fat arraw function ES6 repos

## Template Strings Introduction

This is kinda pain in the Ass to concatenate string and variable 
problem is if we forgot to put + sign anywere that would be not nice.

``Example``

```javaScript

var name = 'Snickers';
var age = 2;
var sentence = 'My dog '+ name + ' is ' + age *7 + 'years old.';

console.log(sentence);

//simple fix is use template string

// template string and templete litral
// use backtiks

var sentence = `My dog ${name} is ${age *7} years old.`;

console.log(sentence);

```

## Creating HTML fragments with Template Literals

> it allow us to do multiple line without any funny business. for Example

```javaScript
var text = "hello there, \
  how are you  \
";
# so puting '\' each line is like adding some more task, so instead
```

``use``

```javaScript
  
   const person = {
    name: 'Gaurav',
    job : 'Programmer',
    city: 'Hamilton',
    bio: 'Gaurav is a really cool guy that loves to teach programming!'
   };


  const markup = `
    <div class="person">
      <h2>
        ${person.name}
        <span class="job">${person.job}</span>
      </h2>
      <p class="location">${person.city}</p>
      <p class="bio">${person.bio}</p>
    </div>
  `
  console.log(markup);
  
  document.body.innerHTML = markup;
```
> you can neast them inside of each other

```javaScript

const dogs = [
  {name: 'Snikkers', age: 2},
  {name: 'Hugo', age: 8},
  {name: 'Sunny', age: 1}
]

const markup = `
    <ul class="dogs">
      ${dogs.map(dog => `<li>${dog.name} is ${dog.age * 7} years old.</li>`).join('')}
    </ul>
`;

console.log(markup);
document.body.innerHTML = markup;

```

> You can write if statement inside template String

```javaScript

  const song = {
    name: 'Dying to live',
    artist: 'Tupac',
    featuring: 'Biggie Smalls'
  }

  const markup = `
    <div class="song">
      <p>
        ${song.name} - ${song.artist}
        ${song.featuring ? `(Featuring ${song.featuring})` : ''}
      </p>
    </div>
  `
  
  document.body.innerHTML = markup;
```

```javaScript

  const song = {
    name: 'Dying to live',
    artist: 'Tupac',
    featuring: ['Biggie Smalls','Eminem','Snoop dog']
  }
  
  
  function renderFeaturing(featuring) {
    return `
      <ul>
        ${featuring.map(feature => `<li>{feature}</li>`).join('')}
      </ul>
    `
  }

  const markup = `
    <div class="song">
      <p>
        ${song.name} - ${song.artist}
        ${song.featuring ? renderFeaturing(song.featuring) : ''}
      </p>
    </div>
  `
  
  document.body.innerHTML = markup;


```

## Tagged Template Literals as function


```javaScript
  
  // strings array will be one larger than values array
  
  function highlight(strings, ...values){
    // debugger;
    let str = '';
    strings.forEach((string, i) => {
      // str += string + (values[i] || '');
      str += `${string} <span class="h1" contenteditable >${values[i] || ''}</span>`;
    });
    return str;
  }
  
  const name = "Snickers";
  const age = 100;
  
  const sentence = highlight` My gog's name is ${name} and he is ${age} years old `;
  console.log(sentence);
  document.body.innerHTML = sentence;
  
```

## Tagged Template Literals as Excersice

```javaScript

const dict = {
    HTML: "Hyper Text Markup Language",
    CSS: "Cascading Style Sheets",
    JS: "JavaScript"
};

function addAbbreviations(strings, ...values) {
    const abbreviated = values.map(v => {
        if(dict[v]){
            return `<abbr title="${dict[v]}">${v}</abbr>`
        }
        return v;
    })
    // console.log(abbreviated);
    return strings.reduce((sentence, string, i) => {
        return `${sentence}${string}${abbreviated[i] || ''}`
    }, '');
}

const first = 'Gaurav'
const last = 'Gupta'

const sentence = addAbbreviations`Hello my name is ${first} ${last} and I love to code ${'HTML'}, ${'CSS'} and ${'JS'} `

```

## Santizing User Data with Tagged Templates

```javaScript
function santize(string, ...values) {
    const dirty = string
        .reduce((prev, next, i) => `${prev}${next}${values[i] ||
             ''}`, '');
    return DOMPurify.sanitize(dirty); // its a library check out.
}

const firstName = 'Gaurav';
const aboutMe = santize`I love to do evil <img src="http://unsplash.it/100/100?random" onload="alert('you got hacked');" />`;

const html = `
    <h3>${firstName}</h3>
    <p>${aboutMe}</p>
`;

const bio = document.querySelector('.bio');
bio.innerHTML = html;

bio; /*? */

```

## New String Methods

```javaScript

  const course = 'RFB2';
  const flightNumber = '20-AC2018-jz';
  const accountNumber = '825242631RT0001';

  const make = 'BMW';
  const model = 'x5';
  const colour = 'Royal Blue';

  // .startsWith()

  course.startsWith('RFB'); /*? */
  flightNumber.startsWith('AC', 3); /*? */

  // .endsWith()

  flightNumber.endsWith('jz'); /*? */
  accountNumber.endsWith('RT', 11); /*? */

  // .includes()

  flightNumber.includes('AC'); /*? */

  // .repeat()

  function leftPad(str, length = 20) {
      return `-> ${' '.repeat(length - str.length)}${str}`;
  }

  console.log(leftPad('BMW'))
  console.log(leftPad('X5'))
  console.log(leftPad('Royal Blue'))

```
## Destructuring Objects

```javaScript
const person = {
    first: 'Gaurav',
    last: 'Gupta',
    country: 'India',
    city: 'Delhi',
    fb: 'gouravkiller876@gmail.com'
};

const {first , last} = person;

first;

const Gaurav = {
    first: 'Gaurav',
    last: 'Gupta',
    links: {
        social: {
            fb: 'https://facebook.com/gauravgupta',
            gm: 'https://gmail.com/v1/u/gouravgupta'
        },
        web: {
            blog: 'https://medium.com/user/gauravgupta'
        }
    }
}

const { fb: facebook, gm: gmail } = Gaurav.links.social;
facebook;

const settings = {width: 300, color: 'black'} //height, fontSize
// const {width, height, color, fontSize} = settings;
// const {width = 100, height = 100, color = 'blue', fontSize = 25} = settings;
// height;

// Some Concreate Example

const {w: width = 400, h: height = 500} = {w: 800};
height; /*? */

```

## Destructing Arrays

```javaScript

const details = ['Gaurav Gupta', 123, 'goonsroom.com'];
const [name, id, website] = details;

name;
id;
website;

const data = 'Basketball,Sport,90210,23';
let [itemName, category, sku, inventory] = data.split(',');

itemName;
category;

const data2 = 'Basketball,Sport,90210,23,Gaurav,Gupta,Cool';
[itemName, category,sku, inventory,...rest] = data2.split(',');
itemName;
rest;

```

## Swapping Variables with Destructuring

```javaScript

let inRing = 'Hulk Hogan';
let onSide = 'The Rock';

inRing;
onSide;

[inRing, onSide] = [onSide, inRing];

inRing;
onSide;

```

## Destructuring Functions - Multiple returns and named defaults

```javaScript

function convertCurrency(amount) {
    const converted = {
        USD: amount * 0.76,
        GPB: amount * 0.53,
        AUD: amount * 1.01,
        MEX: amount * 13.30,
    };
    return converted;
}

const hundo = convertCurrency(100);

console.log(hundo.AUD);
console.log(hundo.MEX);

const {USD, GPB, AUD: Austrilian = 100, MEX, I = 500} = convertCurrency(100);
USD;
I;
Austrilian;


function tipCalc({total, tip = .15, tax = 0.13} = {}) {
    return total + (tip * total) + (tax * total);
}

const bill = tipCalc({total: 200, tip: .2, tax: .13});
console.log(bill);

const bill2 = tipCalc({tax: .13, total: 200});
console.log(bill2);

const bill3 = tipCalc();
console.log(bill3);


```

## The for of Loop in Action

```javaScript

const cuts = ['Chuck','Brisket','Shank','Short Rib'];

for(const cut of cuts) {
    console.log(cut);
}

cuts.entries(); /*? */

const meat = cuts.entries();

meat.next(); /*? */
meat.next(); /*? */
meat.next(); /*? */
    
for(const [i, cut] of cuts.entries()) {
    console.log(`${cut} is the ${i} item`);
}

function addUpNumbers() {
    console.log(arguments);
    let total = 0;
    for (const num of arguments) {
        total += num;
    }
    console.log(total);
    return total;
}

addUpNumbers(10,23,52,34,12,13,123); /*? */

function best(i,o,j){
    console.log(...arguments);
}

best(1,2,[3]);

const name = 'Gaurav';

for (const char of name) {
    console.log(char);
}


const ps = document.querySelectorAll('p');
console.log(ps);
for (const paragraph of ps) {
    paragraph.addEventListener('click', function() {
        console.log(this.textContent);
    })
}


```

## The for of loop

```javaScript

const cuts = ['Chuck', 'Brisket', 'Shank', 'Short Rib'];

Array.prototype.chunk = function(index) {
    this[index] = this[index].toUpperCase();
}

cuts.shop = 'hello'

for (const key in cuts) {
    // prints every thing even prototype methods as well
    console.log(key); /* 0, 1, 2, 3, shop, chunk */
}

for (const cut of cuts) {
    if(cut === 'Brisket') {
        continue;
    }
    console.log(cut); // Chunk, Shank, Short Rib
}

```

## Using for in with Objects

```javaScript

const apple = {
    color: 'Red',
    size: 'Medium',
    weight: 50,
    suger: 10,
}

// for (const prop of apple.entries()) {
//     console.log(prop);
// }

for (const prop in apple) {
    if (apple.hasOwnProperty(prop)) {
        console.log(apple[prop]);        
    }
}

```

## Array.from() and Array.of()

```javaScript

const name = 'Gaurav'; // somthing arraies types || NodeList from DOM
const char = Array.from(name);
const t = char.map(e => e.toUpperCase());
t;

const name2 = 'Saurav';
Array.from(name2,(e) => {
    console.log(e.toUpperCase());
})

function sumAll(a) {
    [...arguments] /*? [2,5] */;
    const args = Array.from(arguments);
    return args.reduce((a,c) => a+c,0);
}

sumAll(2,5); /*? */

const ages = Array.of(12,4,23,56,23);
console.log(ages);


```

## Array. find() and .findIndex()

```javaScript

const products = [
    {
        "_id" : ("5b2d38217d75e2cdcb31cf05"),
        "sold" : 15,
        "name" : "JEM UV7",
        "description" : "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. ",
        "price" : 3500,
        "brand" : ("5b2c11d2d37177aedfd6d962"),
        "shipping" : true,
        "available" : false,
        "wood" : ("5b2c1c81255983b4795f8fda"),
        "frets" : 22,
        "publish" : true,
        "createdAt" : ("2018-06-22T17:55:45.880Z"),
        "updatedAt" : ("2018-06-22T17:55:45.880Z"),
        "__v" : 0
    },
    {
        "_id" : ("5b2d384b7d75e2cdcb31cf06"),
        "sold" : 0,
        "name" : "TELE-ub23",
        "description" : "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. ",
        "price" : 600,
        "brand" : ("5b2c11481470fbaecd159dfd"),
        "shipping" : false,
        "available" : false,
        "wood" : ("5b2c1c0981e781b44909627d"),
        "frets" : 22,
        "publish" : true,
        "createdAt" : ("2018-06-22T17:56:27.270Z"),
        "updatedAt" : ("2018-06-22T17:56:27.270Z"),
        "__v" : 0
    },
    {
        "_id" : "5b2d390d7d75e2cdcb31cf07",
        "sold" : 9,
        "name" : "FR7",
        "description" : "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. ",
        "price" : 1300,
        "brand" : ("5b2c12a4d37177aedfd6d967"),
        "shipping" : false,
        "available" : true,
        "wood" : ("5b2c1c81255983b4795f8fda"),
        "frets" : 24,
        "publish" : true,
        "createdAt" : ("2018-06-22T17:59:41.868Z"),
        "updatedAt" : ("2018-06-22T17:59:41.868Z"),
        "__v" : 0,
    }
]

products[1]; /*? */

let product = products.find(p => p._id === '5b2d390d7d75e2cdcb31cf07');

product;

product = products.findIndex(p => p._id === '5b2d390d7d75e2cdcb31cf07');

product;

```

## Array .some() and .every()

```javaScript

const ages = [32,15,19,12];

// is there at least one adult yn the group?
const adultPresent = ages.some(age => age >= 18);
adultPresent;

// is everyone old enough to drink?
const allOldEnought = ages.every(a => a >= 19);
allOldEnought;

```
