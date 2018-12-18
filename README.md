# javascript-cheat-sheet
JavaScript Cheat Sheet

### Values that equate to false
* false
* 0
* ""
* ''
* null
* undefined
* NaN

### Values that equate to true
* everything not false
* true
* 0.5
* "0"

### JavaScript built-in objects
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects]
* [Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
* [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)
* [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
* [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)
* [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)

### To Create a Web Page
Always have the script tag at the bottom of the body tag.
```
<body>
 ...
  <script src="script.js"></script>
</body
```

### Example Web Page
```
<!DOCTYPE html>
<html>

<head>
  <link rel="stylesheet" href="style.css">
 
</head>

<body>
  <h1 id="h">Hello World!</h1>
  <p id="p">some text here</p>
  <button id="b">OK</button>
  
  <script src="script.js"></script>
</body>

</html>
```

### Accessing elements by id
```
var e = document.getElementById("p");
var h = document.getElementById("h");
var b = document.getElementById("b");
e.innerText = "new Text";
h.innerText = "New Header";
```

### Handling events 
```
function but1() {
  alert("ok clicked");
}

b.addEventListener('click',  but1);
```

### Removing and adding Elements
```
p.style.display = 'none';   // remove it
p.style.display = 'block';  // add it back
```

### Rest Parameters
Able to pass multiple parameters as one 
```
function send(...ids) {
    ids.forEach(element => console.log(element));
}
send(5,3,2,6,8);
```
### Destructuring Arrays
Quick way to assign array elements to one or more variables
```
let ids = [1,8,7,3,23];
let [car1, car2, car3, car4, car5] = ids;
console.log(car5);   // 23

let [first, ...rest] = ids;
console.log(rest);   // [8, 7, 3, 23]

let [,, ...remaining] = ids;   // skip first 2 parameters
console.log(remaining);   // [7, 3, 23]
```
### Destructuring Objects
Quick way to assign object properties to one or more variables
```
let car = {id: 5000, style: 'convertible', year: 1967 };
let {id, style} = car;
console.log(id, style);  // 5000 "convertible"

// Note:  property names must match the destructured variable names, otherwise we get undefined
let car1 = {id1: 5000, style1: 'convertible', year: 1967 };
let id1, style1;
{id1, style1} = car; // unexpected token error due to fact that { } begin and end code blocks as well
({id1, style1} = car1);   // 5000 "convertible"
```

### Spread Syntax
Allows us to take an array and spread out its elements
```
function startCars(car1, car2, car3) {
   console.log(car1, car2, car3);
}

let carIds = [100, 200, 300];
startCars(...carIds);    // passing array to function spreads out array elements into parameters ... 100, 200, 300

let carCodes = 'abc';
startCars(...carCodes); // a, b, c

```

### Determining Variable Type
```
console.log(typeof('hello'));  // string
console.log(typeof(''));       // string
console.log(typeof(""));       // string
console.log(typeof(true));     // boolean
console.log(typeof(4.2));      // number
console.log(typeof(4));        // number (not integer)
console.log(typeof([1,2,3]));  // object (not array)
console.log(typeof({x:1, y:2}));     // object
console.log(typeof(function() {}));  // function

console.log(typeof(null));        // object (not null)
console.log(typeof(undefined));   // undefined
console.log(NaN);                 // number  (strange but true.  Not A Number is typeof number)

let arr = ['hello', true, 4, {x:1, y:2}, [1,2,3], "asd", NaN, null, undefined];
for (let i = 0; i< arr.length; i++) {
    console.log("typeof("+arr[i]+") = "+typeof(arr[i]));
}
```

### Common Type Conversions
```
foo.toString();    // convert to string
Number.parseInt('55');   // convert to number
Number.parseFloat('55.99');  // convert to nummber
```

### Equality
```
console.log('0' == 0);  // true.  auto type conversion
console.log('0' != 0);  // false
console.log('0' === 0);  // false.  strict equality.  no auto type conversion 
console.log('0' !== 0);  // true. strict inequality.  no auto type conversion
```

### Operator Precedence
[MDN Operator Precedence Page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)

### let and const respect Block Scope
```
if (5 === 5) {
    let msg = '5 equal 5';
}
console.log(msg);  // error msg is not defined

if (5 === 5) {
    let msg = '5 equal 5';
}
console.log(msg);  // error msg is not defined
```
- var does not respect block Scope 
- var msg gets hoisted to the top of the scope as if it were defined globally at the top of the .js file
```
if (5 === 5) {
    var msg = '5 equal 5';
}
console.log(msg);  // 5 equal 5
```

### Immediately Invoked Function Expression (IIFE)
```
function a() {
    console.log("in function");  // defined but won't execute unless called
}

// function name not needed for IIFE
(function () {
    console.log("in function");
}) ();
```
```
(function a() {
    console.log("in function");  //defined and immediately executed
}) ();
```

### Closures
Closures allow functions to be available after executing
```
// IIFE returns a closure
let app = ( function() {
    let carId = 123;
    let getId = function() {
        return carId;
    };
    return { getId: getId };  // return object with a getId property whose value is the function getId
}) ();
console.log(app.getId());
```

### Arrow Functions
```
let func = () => 123;       // func takes no parameters
console.log(typeof(func));  // function

let func2 = (a, b) => 123 + a * b;   // func2 takes 2 parameters
console.log(typeof(func2));  // function
console.log(func2(2,3));     // 129
```

### Expanding Objects using Prototypes
```
String.prototype.hello = function() {
    return 'hello ' + this.toString();
};
console.log("fred".hello());   //  hello fred


Number.prototype.power = function(exp) {
    return Math.pow(this, exp);
};
console.log((5).power(2));   // 25
```

### Array Iteration
```
let cars = [
    { carId:123, style:'sedan'},
    { carId:456, style:'convertible'},
    { carId:789, style:'sedan'}
];

cars.forEach( i => console.log(i));     // iterate over array

// filtering elements out of array
let sedans = cars.filter( i => i.style === 'sedan');
console.log(sedans);

// apply a test condition to see if condition holds for every element in the array
let result = cars.every( i => i.carId > 0);
console.log(result);    // true because every element has carId > 0

// find a specific element satisfying a given condition
let carX = cars.find( i => i.carId > 500);
console.log(carX);    //  { carId:789, style:'sedan'}
```

### Classes
```
class Car {
    // define single argument constructor
    constructor(id) {
        this.id = id;
    }
    identify() {
        return `Car Id ${this.id}`;
    }
}
let car = new Car(123);
console.log(car);
console.log(car.identify()); // Car Id 123
```
