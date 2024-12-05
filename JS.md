
# JavaScript

## Printing

```javascript
console.log("Hello, JavaScript")
```

## Variables

### let

```javascript
"use strict";	// prevents use of variables withour declaring it
num = 5;	// error: num is not defined
let num =5;	// valid
```

### const

- Use **`camelCase`** mostly.

- To declare a constant (unchanging) variable, use `const` instead of `let`

	```javascript
	const myBirthday = '18.04.1982';

	myBirthday = '01.01.2001'; // error, can't reassign the constant!
	```

- Declare difficult to remember values (hard-coded) in **UPPERCASE** (community practice), e.g.

	```javascript
	const COLOR_RED = "#F00";
	```

- For others, e.g. constants are _calculated_ in run-time use **lowercase**

	```javascript
	const pageLoadTime = /* time taken by a webpage to load */;
	```
	The value of `pageLoadTime` is not known before the page load, so it’s named normally. But it’s still a constant because it doesn’t change after the assignment.
	
	```javascript
	const BIRTHDAY = '18.04.1982';	// hard-coded
	const AGE = calculateAge(BIRTHDAY); // calculated in runtime	
	```

- Use meaningful and verbose names like `userName` or `shoppingCart`.
	Make names maximally descriptive and concise. Examples of bad names are `data` and `value`.
	For example `ourPlanetName` instead of `planet`,
	to store current user `currentUserName`.

- Use extra variables whenever needed. An extra variable is good, not evil. Browsers optimize code well enough.

## Arithmatic Operations

- [Operator precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_precedence#table)
- `x ** y` means $x^y$
- JavaScript Numbers are Always 64-bit Floating Point
- 
	```javascript
	let x = 123e5;    // 12300000
	let y = 123e-5;   // 0.00123
	```
 - Integers (numbers without a period or exponent notation) are accurate up to 15 digits.
		 
	```javascript
	let x = 999999999999999; // x will be 999999999999999  
	let y = 9999999999999999; // y will be 10000000000000000
	``` 
	Maximum number of decimals is 17.
	Outside the largest possible number, it shows `Infinity` or `-Infinity`
	
	`bigInt` is used for very huge numbers.

	```javascript
	const hugeNum = 68509236539n;	// Add n at last to declare as bigInt
	// You can't mix bigInt with normal number type
	```

- Floating point arithmetic is not always 100% correct
 
	```javascript
	let x = 0.2 + 0.1;	// 0.30000000000000004
	// To solve this, it helps to multiply and divide
	let x = (0.2 * 10 + 0.1 * 10) / 10;
	```

- JavaScript uses the `+` operator for both addition and concatenation. 
	Numbers are added. Strings are concatenated.
	`number` + `string` = `string`

	```javascript
	let x = 10;  
	let y = 20;  
	let z = "The result is: " + x + y;	// The result is: 1020
	```
	```javascript
	let x = 10;  
	let y = 20;  
	let z = "30";  
	let result = x + y + z;	// 102030
	```

- JavaScript will try to convert **numeric strings** to numbers in all numeric operations

	```javascript
	let x = "100";
	let y = "10";
	let z = x / y;	// 10
	let m = 100 / "5";	 // 25
	// IMPORTANT
	// Note "*" or "/" or "-" works, but "+" doesn't, as that means concatenation
	let w = x + y;	//10010
	```

- Trying to do arithmetic with a non-numeric string will result in `NaN` (Not a Number)

	```javascript
	let x = 100 / "Apple";	// NaN
	```
	```javascript
	let x = 100 / "Apple";  
	isNaN(x);	// true
	```
	```javascript
	let x = NaN;  
	let y = 5;  
	let z = x + y;	//NaN
	```
	```javascript
	let x = NaN;  
	let y = "5";  
	let z = x + y;	//NaN5
	```

- JavaScript interprets numeric constants as hexadecimal if they are preceded by `0x`.
	
	```javascript
	let x = 0xFF;
	console.log(x);	//255
	```

- Never write a number with a leading zero (like 07). 
	Some JavaScript versions interpret numbers as octal if they are written with a leading zero.

- 
	```javascript
	let x = 10;	// decimal as default
	let y = x.toString(2);	// base as parameter
	let z = x.toString(8);
	console.log(y,z);	// 1010 12
	```

- `==` (Abstract equality operator) compares after type coercion (conversion)
	`===` (Strict equality operator) compares value without type coercion
	Similarly `!==` is strict non-equality operator
	**Use only strict operators**, it leads to less errors

	```javascript
	console.log( "5" == 5 )   // true
	console.log( "5" === 5 )  // false
	console.log( 5 !== 2+3 )  // false
	```

- To round-off floats,

	```javascript
	let  lotsOfDecimal  =  3.135479876455325;
	let  fixedInt  =  lotsOfDecimal.toFixed(2);
	console.log(fixedInt);	// 3.14
	```

- String to number

	```javascript
	let myNumber = "74";
	myNumber = Number(myNumber);
	```
- Unary `+` or unary `-` converts string to number.

	```javascript
	let num = "5";
	console.log(num, typeof num);	// 3 string
	num = -num;
	console.log(num, typeof num);	// -2 'number'
	```
- `++` or `--` only applies to variables. Doing `5++` will give an error



## Data Types

There are 8 basic data types in JavaScript.

-   Seven primitive data types:
    -   `number` for numbers of any kind: integer or floating-point, integers are limited by `±(253-1)`.
    -   `bigint` for integer numbers of arbitrary length.
    -   `string` for strings. A string may have zero or more characters, there’s no separate single-character type.
    -   `boolean` for `true`/`false`.
    -   `null` for unknown values – a standalone type that has a single value `null`.
    -   `undefined` for unassigned values – a standalone type that has a single value `undefined`.
    -   `symbol` for unique identifiers for objects.
-   And one non-primitive data type:
    -   `object` for more collection of data and more complex data structures.

The `typeof` operator allows us to see which type is stored in a variable.

-   Usually used as `typeof x`, but `typeof(x)` is also possible.
-   Returns a string with the name of the type, like `"string"`.
-   For `null` returns `"object"` – this is an error in the language, it’s not actually an object.

## Strings

- In JavaScript, you can choose single quotes (`'`), double quotes (`"`), or backticks (`` ` ``) to wrap your strings in. All will work.

- Strings declared using backticks are a special kind of string called a [_template literal_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals). In most ways, template literals are like normal strings, but they have some special properties:

	-   you can [embed JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Strings#embedding_javascript) in them
	-   you can declare template literals over [multiple lines](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Strings#multiline_strings)

### Regular Expressions

Inside a template literal `` ` ``, you can wrap JavaScript variables or expressions inside `${ }`, and the result will be included in the string

```javascript
const name = "Chris";
const greeting = `Hello, ${name}`;
console.log(greeting); // "Hello, Chris"
```
In similar way we can do **concatenation**:
```javascript
const one = "Hello, ";
const two = "how are you?";
const joined = `${one}${two}`;
console.log(joined); // "Hello, how are you?"
```
> However, template literals make code more readable.
> [RegExp in details](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions).
> [RegExp in 20 mins](https://youtu.be/rhzKDrUiJVk?si=5QwD6ZD0-RjrAx00).
> [When not to use RegExp](https://softwareengineering.stackexchange.com/questions/113237/when-you-should-not-use-regular-expressions).

We can use expressions in template literals:
```javascript
const song = "Fight the Youth";
const score = 9;
const highestScore = 10;
const output = `I like the song ${song}. I gave it a score of ${
  (score / highestScore) * 100
}%.`;
console.log(output); // "I like the song Fight the Youth. I gave it a score of 90%."
```

### Multiline Strings
Template literals respect the line breaks in the source code:

```javascript
// Only works with backticks `
const newline = `One day you finally knew
what you had to do, and began,`;
console.log(newline);

/*
One day you finally knew
what you had to do, and began,
*/
```

We can also include line break characters (`\n`), it works with quotes too.

### Escape Sequence

To include `"` or `'` or `` ` `` we can use escape sequence `\

```javascript
const bigmouth = 'I\'ve got no balls';
console.log(bigmouth);	// I've got no balls
```

### Number <---> String
To convert string to number:

```javascript
const myString = "123";
const myNum = Number(myString);
console.log(typeof myNum);	// number
```

To convert number to string:

```javascript
const myNum2 = 123;
const myString2 = String(myNum2);
console.log(typeof myString2);	// string
```

## String Methods
All string methods return a new value.
They do not change the original variable.
| Name | Syntax | Notes |
|--|--|--|
| Length | `myString.lenght` |  | 
| Extract Char | `myString.charAt(position)` |  |
| Extract UTF-16 Code | `myString.charCodeAt(position)` |  |
| Index Method | `myString.at(position)` | This is a new addition to JavaScript.<br>We can use -ve indexes too.
| Property Access | `myString[position]` | If no character is found, [ ] returns undefined, while charAt() returns an empty string. |
| Substring | `myString.slice(strat,end)`<br>`myString.slice(pos)` | slices between start and end pos.<br>slices pos to end.<br>If pos -ve, counted from end. |
|  | `myString.substring(start,end)`<br>`myString.substring(pos)` | Same as `slice` but -ve pos is considered `0` |
|  | `myString.substr(start,length)`<br>`myString.substr(pos)` | specifies the **length** of the extracted part<br>Single value slices rest of the string from pos. |
| Upper Case | `myString.toUpperCase()` |  |
| Lower Case | `myString.toLowerCase()` |  |
| Concatenation | `fullName = firstName.concat(" ",surName)` |  |
| Trim | `myString.trim()` | Trims whitespace from both side of string<br>Leaves inner spaces as it is |
|  | `myString.trimStart()` |  |
|  | `myString.trimEnd()` |  |
| Padding | `myString.padStart(no, str)`<br>myString.padEnd(no, str) | Add `no` of `str` to start/end of a string.<br>To pad a number, convert the number to a string first.<br>[Ref](https://www.w3schools.com/jsref/jsref_string_padstart.asp). |
| Repeat | `myString.repeat(count)` | Returns a string with a number of copies of a string. |
| Replace | `myString.replace("Old","New")` | Replaces first "Old" with "New"<br>Case sensitive. |
|  | myString.replace(/New/g,"Old")<br>`myString.replaceAll("Old","New")` | `/g` global flag, to replace all occurrences |
|  | myString.replace(/NEW/i,"Old") | Not case sensitive |
|  | myString.replace(/NEW/i,"Old")<br>myString.replaceAll(/NEW/g,"Old") | We can use [RegExp](https://www.w3schools.com/jsref/jsref_obj_regexp.asp) this way. |
| String ---> Array | `myString.split(" ")`<br>`myString.split("")` | Splits on spaces.<br>Returns array of spaces. |
| Includes | `myStr.includes(substr)` | Returns true/false |
| Search | `myStr.search(substr)` | Searches a string for a value, or Regexp, and returns the index of the match |
| Starts with<br>Ends with | `myString.startWith(substr)`<br>`myString.startWith(substr)` | Returns true/false |

> [Complete list](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) of string methods.

- To compare strings use `===`, to do it case insensitively check all upper once then all lower once, and return their and.

### Evaluate string expression
```javascript
let str = "15*7/12";
console.log(eval(str));	//8.75
```
### String Object <---> Primitive String
To convert a primitive string to an object:
```javascript
let strPrim = "Hello!";
let strObj = new String(strPrim);

console.log(typeof strObj, strObj);	// Object String{'Hello!'}
```
To convert an object to a primitive string:
```javascript
let strObj = new String("Hello!");
let strPrim = strObj.valueOf();

console.log(typeof strPrim, strPrim);	// String Hello!
```

### Emojis and `split("")`
All the characters in string are UTF-16 codes. But emojis are made of more than one code. So while using `split("")` in strings with emojis we shiuld be careful, as it'll break the emoji into several unicodes.


## Conditionals

Any value that is not `false`, `undefined`, `null`, `0`, `NaN`, or an empty string (`''`) returns `true` when tested as a conditional statement.

### Comparison of different types
When comparing values of different types, JavaScript converts the values to numbers:
```javascript
alert( '2' > 1 ); // true, string '2' becomes a number 2
alert( '01' == 1 ); // true, string '01' becomes a number 1
alert( '2' > '12' ); // true, string dictionary comparision
```
**Avoid Problems:**
- The values `null` and `undefined` equal `==` each other and do not equal any other value.
- Be careful when using comparisons like `>` or `<` with variables that can occasionally be `null/undefined`. Checking for `null/undefined` separately is a good idea.	
	> For details refer [this](https://javascript.info/comparison).

### if, else if, else
Basic syntax:
```javascript
if (time < 10) {
  greeting = "Good morning";
} else if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

### Ternary Operator

```JAVASCRIPT
condition ? run this code if true : run this code if false
```
```javascript
const greeting = isBirthday
  ? "Happy birthday Mrs. Smith — we hope you have a great day!"
  : "Good morning Mrs. Smith.";
```
```javascript
let message;

if (login == 'Employee') {
  message = 'Hello';
} else if (login == 'Director') {
  message = 'Greetings';
} else if (login == '') {
  message = 'No login';
} else {
  message = '';
}
```

### Switch Statement
Equality checks are strict `===`

```javascript
let a = 3;

switch (a) {
  case 4:
    alert('Right!');
    break;

  case 3: // (*) grouped two cases
  case 5:
    alert('Wrong!');
    alert("Why don't you take a math class?");
    break;

  default:
    alert('The result is strange. Really.');
}
```


## Logical Operators

### OR ||

-   Evaluates operands from left to right.
-   For each operand, converts it to boolean. If the result is `true`, stops and returns the original value of that operand.
-   If all operands have been evaluated (i.e. all were `false`), returns the last operand.

	```javascript
	let firstName = "";
	let lastName = "";
	let nickName = "SuperCoder";

	alert( firstName || lastName || nickName || "Anonymous"); // SuperCoder
	```

### AND &&
-   Evaluates operands from left to right.
-   For each operand, converts it to a boolean. If the result is `false`, stops and returns the original value of that operand.

	```javascript
	alert( 1 && 2 && null && 3 ); // null
	alert( 1 && 2 && 3 ); // 3, the last one
	```

### NOT !

-  Converts the operand to boolean type: `true/false`.

	```javascript
	alert( "non-empty string" ); // true
	alert( !"" ); // true
	```


## Functions

### Default parameters

If you're writing a function and want to support optional parameters, you can specify default values by adding `=` after the name of the parameter, followed by the default value:

```javascript
function hello(name = "Chris") {
  console.log(`Hello ${name}!`);
}

hello("Ari"); // Hello Ari!
hello(); // Hello Chris!

```

### Anonymous Functions
function with no name, **funciton expression**

```javascript
// Normal
fucntion logkey(event){
	console.log(`You pressed "${event.key}".`);
}
textBox.addEventListener("keydown", logKey);

// Annonymous Functions
textBox.addEventListener("keydown", fuction (event) {
	console.log(`You pressed "${event.key}".`);
});
```

### Arrow Functions
Alternate way to write annonymous functions.
```javascript
// Arrow Functions
textBox.addEventListener("keydown", (event)=> {
	console.log(`You pressed "${event.key}".`);
});

// Only one parameter, we can omit ()
textBox.addEventListener("keydown", event=> {
	console.log(`You pressed "${event.key}".`);
});

// No prameters
let sayHi = () => alert("Hello!");
sayHi();

// Only one return value
const originals = [1, 2, 3];
const doubled = originals.map(item => item * 2);
console.log(doubled); // [2, 4, 6]

// is similar to
function doubleItem(item) {
  return item * 2;
}

```
```javascript
let func = (arg1, arg2, ..., argN) => expression;

let func = function(arg1, arg2, ..., argN) {
  return expression;
};

let sum = (a, b) => a + b;

let double = n => n * 2;
alert( double(3) ); // 6
// roughly the same as: let double = function(n) { return n * 2 }

```
Another example with conditional declaration
```javascript
let welcome = (age < 18) ?
  () => alert('Hello!') :
  () => alert("Greetings!");
```
### Spread syntax, Multiple Parameters
```javascript
const removeFromArray = function(arr, ...args) {
    let newArr = [];
    for(item of arr){
        if(args.includes(item)){
            continue;
        }
        else{
            newArr.push(item);
        }
    }
    return newArr;
};
```

### Default Parameters

```javascript
// New Method
function showMessage(from, text = "no text given") {
  alert( from + ": " + text );
}
showMessage("Ann"); // Ann: no text given
showMessage("Ann", "Hello"); // Ann: Hello

// Old Method

function showMessage(from, text) {
  if (text === undefined) {
    text = 'no text given';
  }
  alert( from + ": " + text );
}

// OR ||
function showMessage(from, text) {
  text = text || 'no text given';
  ...
}
```

### nullish coalescing operator

it’s better when most falsy values, such as `0`, should be considered “normal”

```javascript
function showCount(count) {
  // if count is undefined or null, show "unknown"
  alert(count ?? "unknown");
}
```

### Return
```javascript
function checkAge(age) {
  if (age >= 18) {
    return true;
  } else {
    return confirm('Do you have permission from your parents?');
  }
}
```
- When no return statement function returns `undefined`. 

### Function is a value

In js functions are trated as variables.
```javascript
// Normal method called "Function Declarartion", Most preffered
function sayHi() {
  alert( "Hello" );
}

console.log( sayHi ); // prints the function code
```
```javascript
function sayHi() {
  console.log("Hello");
}

let greet = sayHi; // Assign function to a variable, function expression
greet(); // Hello
sayHi(); // Hello
```
```javascript
let greet = function() {
  console.log("Hi there!");
};
greet(); // Hi there!
```
> Note: Only use function expressions when you need conditional declaration.

-   Function Declarations are processed before the code block is executed. They are visible everywhere in the block.
-   Function Expressions are created when the execution flow reaches them.

### Callback functions

Functions can be passed as values. The idea is that we pass a function and expect it to be “called back” later if necessary.
```javascript
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}

function showOk() {
  alert( "You agreed." );
}

function showCancel() {
  alert( "You canceled the execution." );
}

// usage: functions showOk, showCancel are passed as arguments to ask
ask("Do you agree?", showOk, showCancel);
// Or Annonymous Expression
ask(
  "Do you agree?",
  function() { alert("You agreed."); },
  function() { alert("You canceled the execution."); }
);
```
The arguments `showOk` and `showCancel` of `ask` are called _callback functions_ or just _callbacks_.

### Calling before declaration


A global Function Declaration is visible in the whole script, no matter where it is.

That’s due to internal algorithms. When JavaScript prepares to run the script, it first looks for global Function Declarations in it and creates the functions. We can think of it as an “initialization stage”.

And after all Function Declarations are processed, the code is executed. So it has access to these functions.

For example, this works:

```javascript
sayHi("John"); // Hello, John

function sayHi(name) {
  alert( `Hello, ${name}` );
}
```

The Function Declaration `sayHi` is created when JavaScript is preparing to start the script and is visible everywhere in it.

…If it were a Function Expression, then it wouldn’t work:

```javascript
sayHi("John"); // error!

let sayHi = function(name) {  // (*) no magic any more
  alert( `Hello, ${name}` );
};
```

Function Expressions are created when the execution reaches them. That would happen only in the line `(*)`. Too late.

### Conditional Function Decalrations

```javascript
let age = 16; // take 16 as an example

if (age < 18) {
  welcome();               // \   (runs)
                           //  |
  function welcome() {     //  |
    alert("Hello!");       //  |  Function Declaration is available
  }                        //  |  everywhere in the block where it's declared
                           //  |
  welcome();               // /   (runs)

} else {

  function welcome() {
    alert("Greetings!");
  }
}

// Here we're out of curly braces,
// so we can not see Function Declarations made inside of them.

welcome(); // Error: welcome is not defined
```
We can do:
```javascript
let age = prompt("What is your age?", 18);

let welcome;

if (age < 18) {

  welcome = function() {
    alert("Hello!");
  };

} else {

  welcome = function() {
    alert("Greetings!");
  };

}

welcome(); // ok now
```
or simply
```javascript
let age = prompt("What is your age?", 18);

let welcome = (age < 18) ?
  function() { alert("Hello!"); } :
  function() { alert("Greetings!"); };

welcome(); // ok now
```



## Function Scope


- the variables and other things defined inside the function are inside their own separate **scope**
- The top-level outside all your functions is called the **global scope**. Values defined in the global scope are accessible from everywhere in the code.
- Keeping parts of your code locked away in functions avoids such problems, and is considered the best practice.

For example, say you have an HTML file that is calling in two external JavaScript files, and both of them have a variable and a function defined that use the same name:

html

```javascript
<!-- Excerpt from my HTML -->
<script src="first.js"></script>
<script src="second.js"></script>
<script>
  greeting();
</script>

```
js
``` javascript
// first.js
const name = "Chris";
function greeting() {
  alert(`Hello ${name}: welcome to our company.`);
}

```

js
```javascript
// second.js
const name = "Zaptec";
function greeting() {
  alert(`Our company is called ${name}.`);
}

```

Both functions you want to call are called `greeting()`, but you can only ever access the `first.js` file's `greeting()` function (the second one is ignored). In addition, an error results when attempting (in the `second.js` file) to assign a new value to the `name` variable — because it was already declared with `const`, and so can't be reassigned.

## Call Stack

- The call stack works based on the last-in-first-out (LIFO) principle.
- When you execute a script, the JavaScript engine creates a global execution context and pushes it on top of the call stack.
- Whenever a function is called, the JavaScript engine creates a function execution context for the function, pushes it on top of the call stack, and starts executing the function.
- If a function calls another function, the JavaScript engine creates a new function execution context for the function being called and pushes it on top of the call stack.
- When the current function completes, the JavaScript engine pops it off the call stack and resumes the execution where it left off.
- The script will stop when the call stack is empty.
- it can throw soverflow exception when no of function call exceeds limit. eg. infinite recursive call.
- JavaScript is a single-threaded programming language. This means that the JavaScript engine has only one call stack. Therefore, it only can do one thing at a time.

When executing a script, the JavaScript engine executes code from top to bottom, line by line. In other words, it is synchronous.
```javascript
function add(a, b) {
    return a + b;
}

function average(a, b) {
    return add(a, b) / 2;
}

let x = average(10, 20);

```
![JavaScript Call Stack illustration](https://www.javascripttutorial.net/wp-content/uploads/2019/12/JavaScript-Call-Stack.png)

## Arrays

```javascript
const cars = ["Saab", "Volvo", "BMW"];
```
```javascript
const cars = [];  
cars[0]= "Saab";  
cars[1]= "Volvo";  
cars[2]= "BMW";
```
Array are objects in js.
Objects use **names** to access its "members". In this example, `person.firstName` returns John:
```javascript
const person = {firstName:"John", lastName:"Doe", age:46};
```
### Array Methods

| Method | Syntax | Use |
|--|--|--|
|index|`arr[i]`|to access i'th index. -ve not allowed|
|at|`arr.at(i)`|to accesss index. -ve allowed|
| lenght | `arr.length` ||
|sort|`arr.sort()`|sorts the array|
|tostring|`const fruits = ["Banana", "Orange", "Apple", "Mango"];`<br>`console.log(fruits.toString())`|Banana,Orange,Apple,Mango|
|join|`console.log(fruits.join(" * "))`|Banana * Orange * Apple * Mango|
|push|`arr.push(item)`|add new element to array. LIFO|
|push|`arr.pop()`|pops last entered element. LIFO|
|shift|`fruits.shift()`|removes `"Banana"`, Similar to Dequeue, FIFO |
|unshift|`fruits.unshift(item)`|adds `item` to start |
|concat|`arr1.concat(arr2,arr3)`|Merges multiple arrays|
|copyWithin|`fruits.copyWithin(2, 0)`|Copy to index 2, all elements from index 0:<br>Banana,Orange,Banana,Orange|
|copyWithin|`fruits.copyWithin(2, 0, 2)`|Copy to index 2, the elements from index 0 to 2:<br>Banana,Orange,Banana,Orange,Kiwi,Papaya|
|flat|`const myArr = [[1,2],[3,4],[5,6]];`<br>`const newArr = myArr.flat();`| creates a new array with sub-array elements concatenated to a specified depth<br>1,2,3,4,5,6|
|flatMap|`const myArr = [1, 2, 3, 4, 5, 6];`<br>`const newArr = myArr.flatMap(x => [x, x * 10]);`|first maps all elements of an array and then creates a new array by flattening the array<br>1,10,2,20,3,30,4,40,5,50,6,60|
|splice|`const fruits = ["Banana", "Orange", "Apple", "Mango"];`<br>`fruits.splice(2, 0, "Lemon", "Kiwi");`|`Banana,Orange,Lemon,Kiwi,Apple,Mango`<br>- The first parameter (2) defines the position **where** new elements should be **added** (spliced in).<br>- The second parameter (0) defines **how many** elements should be **removed**.<br>- The rest of the parameters ("Lemon" , "Kiwi") define the new elements to be **added**.|
||`const fruits = ["Banana", "Orange", "Apple", "Mango"];`<br>`fruits.splice(2, 2, "Lemon", "Kiwi");`|Original Array: `Banana,Orange,Apple,Mango`<br>New Array: `Banana,Orange,Lemon,Kiwi`<br>Removed Items:`Apple,Mango`|
|splice() to remove|`const fruits = ["Banana", "Orange", "Apple", "Mango"];`<br>`fruits.splice(0, 1);`|Orange,Apple,Mango|
|toSpliced()|`const months = ["Jan", "Feb", "Mar", "Apr"];`<br>`const spliced = months.toSpliced(0, 1);`|keeps the main array unchanged|
|slice|`const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];`<br>`const citrus = fruits.slice(1);`|Slice out a part of an array starting from array element 1 ("Orange"):<br>`Orange,Lemon,Apple,Mango`|
||`const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];`<br>`const citrus = fruits.slice(3);`|`Apple,Mango`|
||`const citrus = fruits.slice(1, 3);`|`Orange,Lemon`|


## Loops

### for..of loop
```javascript
const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"];

for (const cat of cats) {
  console.log(cat);
}
```

### for...in loop
```javascript
for (key in object) {
  // executes the body for each key among object properties
}
```
```javascript
let user = {
  name: "John",
  age: 30,
  isAdmin: true
};

for (let key in user) {
  // keys
  alert( key );  // name, age, isAdmin
  // values for the keys
  alert( user[key] ); // John, 30, true
}
```
Apart from this `for`, `while`, `do...while` all have regular syntax.
### break & continue
Syntax constructs that are not expressions cannot be used with the ternary operator `?`. In particular, directives such as `break/continue` aren’t allowed there.
```javascript
(i > 5) ? alert(i) : continue; // continue isn't allowed here
```
### Labeled break & continue

```javascript
outer: for (let i = 0; i < 3; i++) {

  for (let j = 0; j < 3; j++) {

    let input = prompt(`Value at coords (${i},${j})`, '');

    // if an empty string or canceled, then break out of both loops
    if (!input) break outer; // (*)

    // do something with the value...
  }
}

alert('Done!');
```
Labels do not allow us to jump into an arbitrary place in the code.

For example, it is impossible to do this:

```javascript
break label; // jump to the label below (doesn't work)

label: for (...)
```

A `break` directive must be inside a code block. Technically, any labelled code block will do, e.g.:

```javascript
label: {
  // ...
  break label; // works
  // ...
}
```

…Although, 99.9% of the time `break` is used inside loops, as we’ve seen in the examples above.

A `continue` is only possible from inside a loop.


