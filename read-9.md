**** forms
* HTML borrows the concept of a form to refer to different elements that allow you to collect information from visitors to your site.
* A user fills in a form and then presses a button to submit the information to the server. The name of each form control is sent to the server along with the value the user enters or selects.
* The server processes the information using a programming. It may also store the information in a database.
* The server creates a new page to send back to the browser based on the information received.
* The server needs to know which piece of inputted data corresponds with which form element.
* `<form>` Form controls live inside a
<form> element. This element
should always carry the action
attribute and will usually have a
method and id attribute too.
* **action** is where the data should be sent to, it exist inside the form tag `<form action-"www.data.com"method="get">`.
* **method**: *get* or *post*. 

