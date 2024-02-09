document.firstElementChild => html
document.firstElementChild.firstElementChild => head
document.firstElementChild.lastElementChild => body 
document.querySelector("ul").lastElementChild.innerText = "Abdul Razzak";
document.getElementById('title')
document.getElementsByClassName("btn") => will give and array
*Important abour querySelector is we can use all CSS selectors as they are and also combined selectors to get to the specific element* ex: document.querySelector(".item") => instead of ".item" we can use "#title" for id or combined with "li a", which will look for li and then a (link) element etc.
document.querySelector('#list a').style.color = "green";
document.querySelector('#list a').style.fontSize = "2rem"; //note the camel notation.
[HTML DOM Style object (w3schools.com)](https://www.w3schools.com/jsref/dom_obj_style.asp)
document.getElementsByTagName('li'); // also gives an array. If so, make sure to use the [] to select even it has only one item in the array.
*Another thing is we can use classList to find out existing classer or remove or add or toggle between classes* ex:
document.querySelector("button").classList.add("invisible"); //adds a class name "invisible" to the button element
document.querySelector("button").classList.remove("invisible") // removes the class
document.querySelector("button").classList.toggle("invisible") // toggles like on/off.
However, make sure to include required style in the CSS in advance instead of using JS to enable as above. ex: 
.invisible {
  visibility: hidden;
}
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