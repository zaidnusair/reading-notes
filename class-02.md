#### Text
##### structural markup:
* when creating a web page you can add tags to the contents of the page to provide extra meaning and better structire the page.
* headings: 6 levels of headings `<h1> <h2> ... <h6>`, `<h1>` for the main heading `<h2>` for subheading and so on.
* paragraphs: you surround the wanted paragraph with `<p>` and `</p>`, each paragraph will be shown in a new line by defult.
* bold and italic: `<b>` for **bold**, `<i>` for *italic*.
* line breaks  & horizontal rules: use `<br />` with out closing tag to brak a line. use `<hr />` to break between themes.
##### semantic markup:
* they do not affect the structure of the page, but used to add extra information to pages.
* strong and ephansis: `<strong>` will be shown in **bold**, `<em>` will be shown as *italic*.
* quoting: for long paragraphs use `<blockquote>` and `<q>` for smaller quots.

#### CSS
```
body {
font-family: Arial, Verdana, sans-serif;}
h1, h2 {
color: #ee3e80;}
p {
color: #665544;}
```
* CSS is used to make the page more attractive.
* you use it by creating rules that controlls the way every box and its content is presented.
* CSS associates style rules with HTML elements.
* a CSS rule contains two part: a *selector* and a *decleration*. 
* the decleration also consists of two parts: a *property* and a *value*.
* differant types of selectors allow you to target rules at differant elements.
* to use an external CSS file use the `<link>` tag :`<link href="css/styles.css" type="text/css"
rel="stylesheet" />` in the head. **this is considered the best practice**.
* to use CSS internally you can use the `<style>` tag, and type youCSS rules in the HTML file.

#### basic JavaScript instruction
```
var today= new Date{);
var hourNow = today.getHours{) ;
var greeting;
if (hourNow > 18) {
greeting= 'Good evening';
else if (hourNow > 12) {
greeting= 'Good afternoon';
else if (hourNow > O) {
greeting 'Good morning';
else {
greeting 'Welcome';
document.write(greeting) ;
```
* a script is a series of statmenets that the computer follows one by one. each instruction is a statment.
* you can add *comments* using `//` and `*/, /*`, to explain what your code does, and to make it easier to follow and read.
* a script needs to store information temporary , it stores that data in *variables*.
* you can declare a variable using `var` to create it, and then giving it a name.
* to assign a value to the variable use the `=` after the name and give it a value.
* types of data :
1. numerical data type: a number.
2. string data type: letters and other charechters.
3. boolean data type: true or false.
* use **arrays** to store a list of variables.
```
var colors;
colors ['white', 'black', ' custom '];
```
##### expressions:
expressions evaluate into a single value.

types of expressions:

1. assign value to a variable. "var color = 'blue';"
2. usetwo or more values to return a single value. "var area = 5*3" 


##### operators:
expressions rely on operators; they allow creating a single value from one or more values.

###### arithmetic operators:


 order of excution: 
* multiplication and devision will be performed before addition and substraction.
* you can use parenthasis if you want to change the order of excution.

###### string operators: 

* there is only one string operator you can use; the addition "+". its used to join strings together (concatenation). if you try any other operation the result will be "not a number" (NaN).
* mixing numbers and strings together:
** you can add a number (place in quotes) to a string, the result will be the number becoming part of a string.

#### operators and loops


##### evalualting conditions

* you use evaluation to compaire a value in the script to what you expect it might be. the result is **true** or **false**.
* " == " *is equal to*, used for compairing two values to see if they're the same.
* " != " *is not equal to*, used for compairing two values to see if they're **not** the same.
* " === " *strict equal to*, used for compairing two values to check if both **data and type** are the same.
* " !== " *strict not equal to*, used for compairing two values to check if both **data and type** are **not** the same.
* " > " *greater than*, used to check if the number on the left is **greater** than the number on the right.
* " < " *less than*, used to check if the number on the left is **less** than the number on the right.
** you can use ">=" and "<=" to include the number on  the right.


##### logical operators

* allows you to compare the results of more than one comparision operator.
* " && " *logical AND*, tests more than one condition, if **both are true** it *return true*.
* " || " *logical OR*, tests at least one condition, if **one is true** it *return true*.
* " ! " *logical NOT*, *inverts* a single *boolean* value.


##### loops

* loops check a condition, if the return is true, it runs a code block.
* the condition keeps checking, as long as the return true the block will keep running, until it returns false, it will exit the block.
* loop types:
 ** FOR: runs a code a specific number of times. uses a counter.
 ** WHILE: used when you dont know the number of times it need to run. doesnt need a counter.
