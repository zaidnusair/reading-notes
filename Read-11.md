#### local storage for web applications
##### before HTML5:
* internet explorer used userData; which allows web pages to store up to 64 KB of data per domain, in a hierarchical XML-based structure.
* Adobe introduced a feature in Flash 6 that gained the unfortunate and misleading name of “Flash cookies.” known as local shared objects.
* Flash cookies allows Flash objects to store up to 100 KB of data per domain.
* Flash-to-JavaScript bridge called AMASS (AJAX Massive Storage System), but it was limited by some of Flash’s design quirks.
* Brad rewrote AMASS and integrated it into the popular Dojo Toolkit under the moniker dojox.storage with Flash 8.
* Flash gives each domain 100 KB of storage “for free.” Beyond that, it prompts the user for each order of magnitude increase in data storage.
* Google launched Gears, an open source browser plugin aimed at providing additional capabilities in browsers.
* Gears provides an API to an embedded SQL database based on SQLite. 
* After obtaining permission from the user once, Gears can store unlimited amounts of data per domain in SQL database tables.
* dojox.storage could auto-detect (and provide a unified interface on top of) Adobe Flash, Gears, Adobe AIR, and an early prototype of HTML5 storage that was only implemented in older versions of Firefox.
* all of these solutions are either specific to a single browser, or reliant on a third-party plugin.

##### after HTML5:
* “HTML5 Storage” is a specification named Web Storage. some browsers refer to it as "Local Storage" or "DOM Storage".
* it’s a way for web pages to store named key/value pairs locally, within the client web browser.
* Unlike cookies, this data is never transmitted to the remote web server.
* it is implemented natively in web browsers, so it is available even when third-party browser plugins are not.
* checking for html5 storage:
```
function supports_html5_storage() {
  try {
    return 'localStorage' in window && window['localStorage'] !== null;
  } catch (e) {
    return false;
  }
}
```
* or you can use **Modernizr** to detect support for HTML5 Storage:
```
if (Modernizr.localstorage) {
  // window.localStorage is available!
} else {
  // no native support for HTML5 storage :(
  // maybe try dojox.storage or a third-party solution
}
```
##### using HTML5 storage:
* You store data based on a named key, then you can retrieve that data with the same key.
* The named key is a string. The data can be any type supported by JavaScript, including strings, Booleans, integers, or floats.
* the data is actually stored as a string.
* If you are storing and retrieving anything other than strings, you will use functions like 'parseInt()' or 'parseFloat()'.
```
interface Storage {
  getter any getItem(in DOMString key);
  setter creator void setItem(in DOMString key, in any data);
};
```
* Instead of using the getItem() and setItem() methods, you can simply use square brackets.
```
var foo = localStorage.getItem("bar");
// ...
localStorage.setItem("bar", foo);
```
***becomes***
```
var foo = localStorage["bar"];
// ...
localStorage["bar"] = foo;
```
* for removing the value for a given named key, and clearing the entire storage area:
```
interface Storage {
  deleter void removeItem(in DOMString key);
  void clear();
};
```
* to get the total number of values in the storage area, and to iterate through all of the keys by index (to get the name of each key):
```
interface Storage {
  readonly attribute unsigned long length;
  getter DOMString key(in unsigned long index);
};
```
* key() with an index that is not between 0–(length-1), the function will return null.
##### tracking changes to HTML5 storage area:
* The storage event is fired on the window object whenever `setItem()`, `removeItem()`, or `clear()` is called and *changes something*.
* to keep track programmatically of when the storage area changes, you can **trap the storage event**.
* to hook the storage event, you’ll need to check which event mechanism the browser supports.
```
if (window.addEventListener) {
  window.addEventListener("storage", handle_storage, false);
} else {
  window.attachEvent("onstorage", handle_storage);
};
```
* for IE use `window.event` instead of `handle_storage`:
```
function handle_storage(e) {
  if (!e) { e = window.event; }
}
```
* The storage event is not cancelable. From within the `handle_storage` callback function, there is no way to stop the change from occurring
##### limitations to current browsers:
1. “5 megabytes” is how much storage space each origin gets by default.
2. “QUOTA_EXCEEDED_ERR” is the exception that will get thrown if you exceed your storage quota of 5 megabytes.
3. “No” is the answer to the next obvious question, “Can I ask the user for more storage space?”

##### HTML5 storage in action:
* with HTML5 Storage, we can save the progress locally, within the browser itself.
* if you're playing a game for example and you made a few moves, then closed the browser tab, then re-opened it. If your browser supports HTML5 Storage, the page should magically remember your exact position within the game, including the number of moves you’ve made, the position , and even whether a particular piece is selected.
* Every time a change occurs within the game, we call this function:
```
function saveGameState() {
    if (!supportsLocalStorage()) { return false; }
    localStorage["halma.game.in.progress"] = gGameInProgress;
    for (var i = 0; i < kNumPieces; i++) {
	localStorage["halma.piece." + i + ".row"] = gPieces[i].row;
	localStorage["halma.piece." + i + ".column"] = gPieces[i].column;
    }
    localStorage["halma.selectedpiece"] = gSelectedPieceIndex;
    localStorage["halma.selectedpiecehasmoved"] = gSelectedPieceHasMoved;
    localStorage["halma.movecount"] = gMoveCount;
    return true;
}
```
*  it uses the `localStorage` object to save whether there is a game in progress (`gGameInProgress`, a Boolean).
*  Using HTML5 Storage, the `resumeGame()` function checks whether a state about a game-in-progress is stored locally. If so, it restores those values using the localStorage object.
```
function resumeGame() {
    if (!supportsLocalStorage()) { return false; }
    gGameInProgress = (localStorage["halma.game.in.progress"] == "true");
    if (!gGameInProgress) { return false; }
    gPieces = new Array(kNumPieces);
    for (var i = 0; i < kNumPieces; i++) {
	var row = parseInt(localStorage["halma.piece." + i + ".row"]);
	var column = parseInt(localStorage["halma.piece." + i + ".column"]);
	gPieces[i] = new Cell(row, column);
    }
    gNumPieces = kNumPieces;
    gSelectedPieceIndex = parseInt(localStorage["halma.selectedpiece"]);
    gSelectedPieceHasMoved = localStorage["halma.selectedpiecehasmoved"] == "true";
    gMoveCount = parseInt(localStorage["halma.movecount"]);
    drawBoard();
    return true;
}
```
* The most important part of this function is the caveat: Data is stored as strings. If you are storing something other than a string, you’ll need to coerce it yourself when you retrieve it.
```
localStorage["halma.game.in.progress"] = gGameInProgress;
```
* in the resumeGame() function, we need to treat the value we got from the local storage area as a string and manually construct the proper Boolean value ourselves:
```
gGameInProgress = (localStorage["halma.game.in.progress"] == "true");
```
##### competing visions:
* A new API has been standardized and implemented across all major browsers, platforms, and devices.
*  Web SQL Database (formerly known as “WebDB”) provides a thin wrapper around a SQL database, allowing you to do things like this from JavaScript:
```
openDatabase('documents', '1.0', 'Local document storage', 5*1024*1024, function (db) {
  db.changeVersion('', '1.0', function (t) {
    t.executeSql('CREATE TABLE docids (id, name)');
  }, error);
});
```
*  most of the action resides in the string you pass to the executeSql method.
* This string can be any supported SQL statement, including SELECT, UPDATE, INSERT, and DELETE statements. It’s just like backend database programming, except you’re doing it from JavaScript.
* you use methods provided by the object store to open a cursor on the database named “USERS,” enumerate through the records, filter out records for inactive users, and use accessor methods to get the values of each field in the remaining records. An early walk-through of IndexedDB is a good tutorial of how IndexedDB works, giving side-by-side comparisons of IndexedDB and Web SQL Database.


