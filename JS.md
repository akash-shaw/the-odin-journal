# JavaScript

## Printing

```js
console.log("Hello, JavaScript")
```

## Variables

### let

```js
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

	```js
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
	```js
	let x = 123e5;    // 12300000
	let y = 123e-5;   // 0.00123
	```
 - Integers (numbers without a period or exponent notation) are accurate up to 15 digits.
		 
	```js
	let x = 999999999999999; // x will be 999999999999999  
	let y = 9999999999999999; // y will be 10000000000000000
	``` 
	Maximum number of decimals is 17.
	Outside the largest possible number, it shows `Infinity` or `-Infinity`
	
	`bigInt` is used for very huge numbers.

	```js
	const hugeNum = 68509236539n;	// Add n at last to declare as bigInt
	// You can't mix bigInt with normal number type
	```

- Floating point arithmetic is not always 100% correct
 
	```js
	let x = 0.2 + 0.1;	// 0.30000000000000004
	// To solve this, it helps to multiply and divide
	let x = (0.2 * 10 + 0.1 * 10) / 10;
	```

- JavaScript uses the `+` operator for both addition and concatenation. 
	Numbers are added. Strings are concatenated.
	`number` + `string` = `string`

	```js
	let x = 10;  
	let y = 20;  
	let z = "The result is: " + x + y;	// The result is: 1020
	```
	```js
	let x = 10;  
	let y = 20;  
	let z = "30";  
	let result = x + y + z;	// 102030
	```

- JavaScript will try to convert **numeric strings** to numbers in all numeric operations

	```js
	let x = "100";
	let y = "10";
	let z = x / y;	// 10
	let m = 100 / "5";	 // 25
	// IMPORTANT
	// Note "*" or "/" or "-" works, but "+" doesn't, as that means concatenation
	let w = x + y;	//10010
	```

- Trying to do arithmetic with a non-numeric string will result in `NaN` (Not a Number)

	```js
	let x = 100 / "Apple";	// NaN
	```
	```js
	let x = 100 / "Apple";  
	isNaN(x);	// true
	```
	```js
	let x = NaN;  
	let y = 5;  
	let z = x + y;	//NaN
	```
	```js
	let x = NaN;  
	let y = "5";  
	let z = x + y;	//NaN5
	```

- JavaScript interprets numeric constants as hexadecimal if they are preceded by `0x`.
	
	```js
	let x = 0xFF;
	console.log(x);	//255
	```

- Never write a number with a leading zero (like 07). 
	Some JavaScript versions interpret numbers as octal if they are written with a leading zero.

- 
	```js
	let x = 10;	// decimal as default
	let y = x.toString(2);	// base as parameter
	let z = x.toString(8);
	console.log(y,z);	// 1010 12
	```

- `==` (Abstract equality operator) compares after type coercion (conversion)
	`===` (Strict equality operator) compares value without type coercion
	Similarly `!==` is strict non-equality operator
	**Use only strict operators**, it leads to less errors

	```js
	console.log( "5" == 5 )   // true
	console.log( "5" === 5 )  // false
	console.log( 5 !== 2+3 )  // false
	```

- To round-off floats,

	```js
	let  lotsOfDecimal  =  3.135479876455325;
	let  fixedInt  =  lotsOfDecimal.toFixed(2);
	console.log(fixedInt);	// 3.14
	```

- String to number

	```js
	let myNumber = "74";
	myNumber = Number(myNumber);
	```
- Unary `+` or unary `-` converts string to number.

	```js
	let num = "5";
	console.log(num, typeof num);	// 3 string
	num = -num;
	console.log(num, typeof num);	// -2 'number'
	```
- `++` or `--` only applies to variables. Doing `5++` will give an error
- Backticks are “extended functionality” quotes. They allow us to embed variables and expressions into a string by wrapping them in `${…}`, for example:

	```js
	let name = "John";

	// embed a variable
	alert( `Hello, ${name}!` ); // Hello, John!

	// embed an expression
	alert( `the result is ${1 + 2}` ); // the result is 3
	```
	Note: It can only be done in backticks.

- The special `null` value does not belong to any type. It is not a “reference to a non-existing object” or a “null pointer” like in some other languages. It’s just a special value which represents “nothing”, “empty” or “value unknown”.