## HTML & CSS

CSS frameworks are pre-prepared software frameworks that are meant to allow for easier, more standards-compliant web design using the Cascading Style Sheets language. Most of these frameworks contain at least a grid.

* to set the view port of the page so that it looks well on every device:
``` html
<meta name="viewport" content="width=device-width,initial-scale=1">
```
* css allow the element to overflow of it's container so to prevent this use relative width and positions instead of absolute, a good practice

``` css
img, embed,
object, video {
    max-width: 100%;
}
```

* calc is used to calculate the width(or height) of an element element:

``` css
div {
  width: calc(100%-10px);
}
img {
  float: left;
  margin-right: 10px;
  width: calc((100% - 20px)/3);
}
```
**Note:** There MUST be a space on each side of the + and - operators. (A space is not required around * and / as the problem is an ambiguity around negation.) For example: calc(100px - 10%) will work. calc(100px-10%) will not.

* The last-of-type selector matches every element that is the last child, of a particular type, of its parent.
``` css
img: last-of-type {
  margin-right: 0;
}
```
to give style to a form element:
``` css
input[type=text] {
  width: 200px;
}
input[type=submit] {
  font-size: 24px;
}
```

* vh unit


``` html
<h1> this is a h1 tag </h1>
<h2> this is a h2 tag </h2>
<h3> this is a h3 tag </h3>
<h4> this is a h4 tag </h4>
```
> <h1> this is a h1 tag </h1>
> <h2> this is a h2 tag </h2>
> <h3> this is a h3 tag </h3>
> <h4> this is a h4 tag </h4>

* font color:
``` html
<font color="red"> red color </font>
```
### <font color="red"> red color </font>
___

* class used to help us in writing css file ex:-
``` html
<p class="any_name"> this is class </p>
<!-- then in the css file -->
```
``` css
.any_name {
    background: green;
}
```

<style type="text/css">
    .rr {
        background: peachpuff;
        color: black;
    }
</style>
<p class="rr"> this is black text on peachpuff background</p>

* we can also use id instead of class but id couldn't be used more than once in the same page
* comment
``` html
<!--This is a comment.-->
```
### forms:
example of simple form:
```html
<form>
  <input>
  <input type="text" name="q" value="ahmed" placeholder="name">
</form>
```
<input type="text" name="q" value="ahmed" placeholder="name">

there are number of attributes you can add to input element
the most important one is type some examples of type:
* radio
* checkbox
* submit
* password

to create a dropdown menu:
``` html

```


* to add button:
``` html
<button>click here</button>
```
<button>click here</button>



___

# <center>**<font color="brown"> CSS</font>**</center> </h1>

* there are 3 ways to write css style:
    * inline: inside the tag.
    * internal: at the top of the html file.
    * external: in separate file.

* class: is a name of a certain type of text



<br><br><br><br>
