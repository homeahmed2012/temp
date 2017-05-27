# <center>__<font color="brown">javascript</font>__</center> </h1>

* there are many ways to write javascript one is inline:
``` javascript
<button onclick="alert('Hi')">click me</button>
```
<button onclick="alert('Hi')">click me</button>
* another way is internal:
``` javascript
<button id="mybutton">click me</button>
<script type="text/javascript">

    document.getElementById("mybutton").onclick = function(){
        alert('Hi');
    }

</script>
//another example
<p id="text">some text</p>
<script type="text/javascript">
    alert(document.getElementById("text").innerHTML);
</script>
```
in this method it is prefer to put the script at the end of the body or in head section.

* the third way is to use external file:

``` html
<script src="test.js"></script>
```

* to write a comment:
``` javascript
//this is a comment
/*
this is a multiline comment
*/
```
* to create variable:
``` javascript
var name = "ahmed";
```
* to add element t"o the page:
``` javascript
document.write("hello")
```
* to get the device pixel retio in chrome console:
``` javascript
window.devicePixelRatio
```

* example to show date and time on click button
``` html
<button type="button" onclick="document.getElementById('demo').innerHTML = Data()">
  click here to show data and time
<button>
<p id="demo"></p>
```
