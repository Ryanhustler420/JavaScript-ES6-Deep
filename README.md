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


































