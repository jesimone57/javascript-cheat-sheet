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
* Math
* Date
* String
* Number
* JSON

### Example HTML
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
  
