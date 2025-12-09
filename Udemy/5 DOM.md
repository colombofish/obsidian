DOM is structured based, and if a page is rendered to a browser then all of its elements are put in a tree based structure, which is called DOM with objects. This task is done by the browser automatically. 
Similar to the CSS, the JS also can be included as "inline, internal or external". 
ex: \<body onload="alert('Hello');">\</body> ==For inline code, we add the JS in "", and internal string in ''. However, best to avoid internal JS in a page==
\<script>alert("Hello");\</script> ==preferably this internal or external JS can be called placing below the body content==
\<script src="./index.js" charset="utf-8">\</script> ==this enables to have external JS file==

So, in the console, we can check/inspect the structure using below sample methods:
document.firstElementChild => html
document.firstElementChild.firstElementChild => head
document.firstElementChild.lastElementChild => body 
document.querySelector("ul").lastElementChild.innerText = "Abdul Razzak"; //Note that querySelector returns a single element. 
So, we can even manipulate the colors. See the sample below:
/*var lastElementList = document.querySelector("ul").lastElementChild;
lastElementList.style.color = "red"; or
document.querySelector("input").click() <= selects the checkbox or unselect it*/
document.getElement==s==ByTagName("li"); //lists all items with the TagName 'li'. So, make sure to pick the correct item by providing the index within ==[]== to manipulate the correct item.
document.getElementById('title') //by a tag name
document.getElement==s==ByClassName("btn") => also give an array or list of items.
*Important abour querySelector is we can use all CSS selectors as they are and also combined selectors to get to the specific element* ex: document.querySelector(".item") => instead of ".item" we can use "#title" for id or combined elements of "li a", which will look for li and then for a (link) element.
==In General querySelector and querySelectorAll will be a good choice if we don't want to modify much the html, css elements by adding more id's classes etc. as we can combine multiple elements, ids and classes through the querySelector==
document.querySelector('#list a').style.color = "green";
document.querySelector('#list a').style.fontSize = "2rem"; //note the camel notation.
[HTML DOM Style object (w3schools.com)](https://www.w3schools.com/jsref/dom_obj_style.asp)
document.getElementsByTagName('li'); // also gives an array. If so, make sure to use the [] to select even it has only one item in the array.
\<li class="item">\<strong class="bold">Second\</strong>\</li> 
For the above ex: we can use => document.querySelector("strong.bold"); this query combination if both categories (element strong and class .bold) within the same element, not child of something. 
document.querySelectorAll(".item"); <= this will give a list of items satisfying the ".item" class.

==Note, the JS names in camel notation unlike in the CSS. Ex: for CSS name "font-size", the JS name will be fontSize. So, make sure to check for the correct name on Internet. Also, the values should be placed within "" as string in JS. An ex. below==
document.querySelector(".btn").style.backgroundColor = "yellow";

*Use classList to find out existing class, then we can add / remove / toggle between classes, this is a fantastic alternative instead of directly changing the properties using JS for changing attributes of the elements. So, the idea is to define all required properties of an element via classes in CSS even that class or element is not in the initial webpage. Later, when that class gets created by clicking on something or as an action of another through JS (Ex classList.add / classList.toggle ) then it acquires the defined properties from the CSS file. Below some samples for adding or toggling:
document.querySelector("button").classList // => DOMTokenList ['btn', value: 'btn']. Then, we add classes to that as below:
document.querySelector("button").classList.add("invisible"); //adds a class name "invisible" to the button element
document.querySelector("button").classList.remove("invisible") // removes the class
document.querySelector("button").classList.toggle("invisible") // toggles like on/off.
So, when you have already included the required style in the CSS in advance, that will reflect on the page. Ex. of a class in CSS: 
.invisible {
  visibility: hidden;
}
/* document.querySelector("a").attributes; provides all the attrib. that r currently attached to it */
/* document.querySelector("a").getAttribute("href") to get one of the attributes value. Then  */
/* document.querySelector("a").setAttribute("href", "https://www.mcb.co.uk"); to change it's value */
We can also use setTimeout() to remove the class as below:

function highlightKey(key) {
  document.querySelector(`.${key}`).classList.toggle("pressed");
  setTimeout(() => {
    document.querySelector(`.${key}`).classList.toggle("pressed");
    console.log('0.3 sec delay');
  }, 300);
}
Suppose we have an html as <h1 id="title"><strong>Hello</strong></h1>
document.getElementById('title').textContent; // outputs: 'Hello', where as 
document.getElementById('title').innerHTML; // outputs (click to see): '<strong>Hello</strong>'

*We can also manipulate attributes*
document.querySelector('li a').attributes('href'); // displays all attributes on this selector.
document.querySelector('li a').getAttribute('href'); // get the value of 'href' attribute.
document.querySelector('li a').setAttribute('href', 'https://www.bing.com'); // sets it.

If we wanna wait for events such as 'button click', 'key pressed', 'mouse over an element' etc., then we need to use an Event Listner. An Ex. is below: 
document.querySelector("button").**addEventListntener**("click", handleClick) /*Look for MDN docs for more details on EventListener.*/
==Note, we are only passing the name of a f-n (handleClick) above, not calling it. Instead, if we add a () above, that will immediately call for it==
function handleClick() {
 alert("I have clicked"); /*a simple f-n for demo purpose*/
}

Another way of writing above code is below:
document.querySelector("button").**addEventListntener**("click", function () {
	alert("I got clicked"); /*this we call an anonymous f-n*/
})
Similarly, document.querySelectorAll("button") provides list of all "button" items. So,
for (let i = 0; i < document.querySelectorAll(".drum").length; i++) {
  document.querySelectorAll("button")[i].addEventListener("click", function () {
    alert("I got clicked");
  });
}
**Playing a sound file in JS**
if (i=\==0) {
    var audio = new Audio('./sounds/tom-1.mp3');
    audio.play();
  }
  The identity of the button, which triggered the event can be referred by =='this' object==
So, inside the above Listener f-n, we can have if (this.innerHTML == w) { }.

###### Targetting an element using Event Listener
buttonsList[i].addEventListener("click", (event) => {
    var clickedButtonId = event.target.id;
    var audio = new Audio("sounds/" + clickedButtonId + ".mp3");
    audio.play();
    });
 