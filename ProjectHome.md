There are many Library's that have already covered many things, **Karat** focuses on manipulating data structures but provides some basic DOM functions.

**karat** is a data structure manipulating function library that chains those functions with DOM events and handlers.<br> It can also retrieve or pass DOM objects, swap values, set values, trigger other functions and disable the handler all in the same function call.<br>
<br>
We can also map DOM elements to event handlers via external js file helping keep the main HTML document nice and tidy.<br>
<br>
<i>Use <b>$k</b> to access the karat object.</i> <br>

<br>

<b>$k.click().chunk()</b><br>        return a chunk of an array <br><br>
<b>$k.click().mdim()</b><br>         return multidimensional array <br><br>
<b>$k.step()</b> <br>                    move thru an array like a cursor and pass the element to a function <br><br>
<b>$k.combine()</b> <br>             return single array with alternating elements of two arrays <br><br>
<b>$k.click.other()</b> <br>         return every other element of an array even or odd <br><br>
<b>$k.click.unique()</b> <br>        return array with duplicates removed<br>
<br><br>
<b>$k.click().every()</b><br>        apply some function to every element in an array<br>
<br><br>
<b>$k.click().map()</b><br>          return new array after apply some function to every element<br>
<br><br>
<b>$k.click.json()</b><br>           return values from JSON structure <br><br>
<b>$k.inArray()</b><br>              returns true/false if found in Array also pass to function in third argument, if true is passed as 4th arg the handler is disabled.<br><br>
<b>$k.click().set()</b><br>          set text or HTML on an element <br><br>
<b>$k.click().show()</b><br>         inspect a value on an element <br><br>
<b>$k.click().swap()</b><br>         swap values between elements <br><br>
<b>$k.get().pass()</b><br>           retrieve an element then pass to a function <br><br>
<b>$k.get().element</b> <br>         retrieve an element <br><br>
<b>$k.on()</b> <br>                  call a function on any event <br><br>
<b>$k.extern()</b> <br>              using config.js file to map multiple Elements / Handlers / Data config.js <br><br>
<b>$k.about()</b> <br>               credits <br><br>


$k.click('element') Takes element ID or Name, function, boolean or chained function call.<br>
<br><br>
eg: <br>
$k.click('div2',function (){<br>
<blockquote>alert('access a Div's HTML using 'this': '+ this.innerHTML)<br>
})</blockquote>

If true the element / click handler will be disabled<br>
If two functions are passed it acts like a trigger each function is executed sequentially.<br>
<br><br>
<b>Array functions:</b><br>

<br><b>chunk</b> <br>
$k.chunk(array, 3) returns an array in chunks specified by size<br>
<br><br><b>mdim</b> <br>
$k.mdim(array, 2) takes are array and int, creates n amount of arrays based on size of each inner array you want.<br>
<br><b>step</b> <br>
$k.step(new Array('a','b','c'), alert) use 'click' event or left / right arrow keys to step thru an array.<br>
$k.click('div2').step(new Array('a','b','c'), stepResult)<br><br>
using keyboard arrow keys: <br>
eg: $k.step(new Array('a','b','c'), stepResult)<br>
<br><br>
<b>combine</b><br>
var a = [1,2,3]<br>
var b = [4,5,6]<br>
alert( $k.combine(a, b) ) <br>
result of combine: > 1,4,2,5,3,6 <br><br>
<b>other</b> <br>
$k.click('div').other(new Array('apple','banana','orange','pear'), 'even')<br><br>
Result of other > apple, orange <br>
$k.other(new Array('apple','banana','orange','pear'), 'odd') <br>
Result of other > banana, pear <br><br>
eg:  $k.click('btn3', someFunction).other(myArray, 'even')<br>
<br> returns every even numbered array element you can also get every other odd index<br>
<br> only works on numerically indexed arrays.<br>
<br><br>
<b>unique</b><br>
$k.click('div2', someFunction, true).unique(new Array('a','b','b','d','e','f'))<br>
Result > a,b,d,e,f<br>
<br><br>
<b>every</b><br>
$k.click('div2').every(new Array('a','b','c'), function(obj){ alert( "APPLE: "+obj ) }, true )<br>
<br><br>Or as standalone function <br>
$k.every(new Array('a','b','c'), function(obj){ alert( "APPLE: "+ obj ) } )<br>
<br><br>
<b>map</b><br>
optional callback for map<br>
function map_result( result ){<br>
<blockquote>alert('map_result > ' +result)<br>
}<br>
<br>
$k.click('div2', function me( <i>array ){<br>
<blockquote>//</i>array = <i>array + "foo" //do something to the array and return new one</i><br>
<i>array =new Array(</i>array + ":bar")  //or do something and return multi-dimensional Array<br>
return <i>array<br>
</blockquote>}<br>
).map(new Array('a','b','c','d'), map_result)<br></i><br><br>
<b>json</b> <br>
$k.click('div2', someFunction).json(employees.sales, 'firstName') //, true<br>
<br><br>
Or as standalone function<br>
eg: alert( $k.json(employees.sales, 'firstName') )<br>
<br><br>
<b>json example:</b> var employees = {<br>
<blockquote>"accounting" : [   //accounting is an array in employees.<br>
<blockquote>{ "firstName" : "John",<br>
<blockquote>"lastName"  : "Doe",<br>
"age"       : 23 },</blockquote></blockquote></blockquote></blockquote>

<blockquote>{ "firstName" : "Mary",<br>
<blockquote>"lastName"  : "Smith",<br>
<blockquote>"age"       : 32 }<br>
</blockquote></blockquote><blockquote>], // End "accounting" array.<br>
</blockquote></blockquote><blockquote>"sales"   : [<br>
<blockquote>{ "firstName" : "Sally",<br>
"lastName"  : "Green",<br>
<blockquote>"age"       : 27 },</blockquote></blockquote></blockquote>

<blockquote>{ "firstName" : "Jim",<br>
<blockquote>"lastName"  : "Galley",<br>
"age"       : 41 }<br>
</blockquote>]<br>
</blockquote><blockquote>}<br>
<br>
function jsonFunction(a, b){<br>
</blockquote><blockquote>alert(a + ' : ' + b) <br>
}<br>
$k.click('div2', jsonFunction).json(employees.sales, 'firstName') //true<br>
<br><br>
<b>or as use as standalone with no click handler</b> <br>
alert( $k.json(employees.sales, 'firstName') ) <br>
<br>If pass in true as third argument this will alert out each property and value.<br>
<br><br><b>Other methods</b><br><br>
<b>$k.click().swap()</b><br>
$k.click(element).swap(elementOne, elementTwo) for changing the value of an Element with another. <br><br>
<b>$k.inArray()</b><br>
$k.inArray(new Array('a','b','c'), 'a', inArrayFunction) <br>
$k.click('div2').inArray(new Array('a','b','c'), 'a', inArrayFunction, true)<br>
<br><br>
<b>$k.click().set()</b><br>
$k.click(element).set('some data') changes HTML or text values.<br><br>
<b>$k.click().show</b><br>
displays current elements HTML or values, pass true to disable.<br>
$k.click('btn3', someFunction, true).show()<br>
<br><br>
<b>$k.click().get().pass()</b><br>
eg: $k.click('div2', functionTwo).get("button1").pass(function5)<br>
<br><br>
<b>$k.on()</b> <br> Takes an event type and object of element/handlers<br>
<br> $k.on('mouseover', { "btn3":funtion1, "btn2":function2 } )<br>
<br><br> <b>$k.extern()</b> <br>
$k.extern('config.js', 'click') this will execute whatever is defined in the config.js file<br>
<br><br>
<b>note</b> if extern() is used and you have a function defined in the html doc<br>
with the same name as in the config.js the config file will win