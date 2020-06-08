#### Lists
* types of lists:
1. ordered lists: using `<ol>` for create it, and `<li>` for each list item. they will appeare numbered.
2. unordered lists: using `<ul>` for create it, and `<li>` for each list item. they will appeare without numbers.
3. definition lists: using `<dl>` to create the list, and `<dt>` to list the item you want to define, and `<dd>` to define it.

* nested lists: you can nest a list inside another, it will appeare as a sub-list.

#### boxes
* each HTML element has its own box. you can controll the box using CSS.
* you can control the box's propereties like dimentions, overflowing content.
* box appearance properities:
1. border: separate a box's edge from another.
2. margin: gap between borders of boxes.
3. padding: space between the box and its content. can increase readability.
* border-width can be set to thin, thick and medium, it can also have a px value. you can assign different width to the box boxs borders.
* border-style can be set to solid, sotted, dashed rooved and others, you can assign different styles to each border.
* you can change the inline element to block and vise versa using `display` properety.
* you can hide or show bixed using `visabiity`.
* `border image` property applies an image to the border of any box.
* `box-shadow property allows you to add a drope shadow around a box. 
* you can round the corners of a box using `border-raduis`.

#### switch statements
```
switch (level) {
case 1:
msg = 'Good luck on the first test ' ;
break;
case 2:
msg = 'Second of three - keep going!';
break;
case 3:
msg = ' Final round, almost there!';
break;
default :
msg = 'Good l uck!';
break;}
```
* a switch statement starts witha variable called *switch* value. 
* each *case* indicates a possible value for this variable and the code it should run if the result is true.
* if a match is found unlike *if statment*; the code is run, then the `break` stops the rest of the `switch` statement from running. (better performance than multiple if statements).

#### logical operators

* allows you to compare the results of more than one comparision operator.
* " && " *logical AND*, tests more than one condition, if **both are true** it *return true*.
* " || " *logical OR*, tests at least one condition, if **one is true** it *return true*.
* " ! " *logical NOT*, *inverts* a single *boolean* value.


#### loops

* loops check a condition, if the return is true, it runs a code block.
* the condition keeps checking, as long as the return true the block will keep running, until it returns false, it will exit the block.
* loop types:
 ** FOR: runs a code a specific number of times. uses a counter.
 ** WHILE: used when you dont know the number of times it need to run. doesnt need a counter.
