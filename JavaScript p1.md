**querySelector():** this method takes a CSS selector as an argument and returns the first element that matches that selector. 
ex1: let h1 = document.querySelector("h1"); //selects an element
ex2: let button1 = document.querySelector('#button1'); //selects id

`button` element has a special property called onclick, which can be accessed with dot notation. 
```js
button.onclick = goStore();
```
const locations = [
  {
    'button functions': [goStore, goCave, fightDragon],
  }
];
console.log(locations[0]['button functions'])// to access a string in an object
shift() method of an array removes the 1st object from the array and returns it.

monsterStats.style.display = 'block'; // assuming the div element defined as monsterStats in the code. Use 'none' to hide.
`split()` method splits a string into an array of substrings and returns new array. Passing an empty string into the `split` method will split the string into an array of individual characters.

Regex in JavaScript is indicated by a pattern wrapped in forward slashes – ex:

```js
const regex = /hello/;
```
const regex = /\+-\s/; //pattern + and minus in regex. To add a space use '\s';
str.replace(regex, ""); See notes in 02CalorieCounter project for more details. 

/ Get the first <li> element inside an <ul> element
var li = document.querySelector("ul li"); // note both parameters are targeted. 
let message = prompt("Compose your message": ); //this allows to collect information typed in into the message var

*Slicing and extracting part of a string*
name = "Abdul";
name.slice(0,1) => this gives the first char of the name string i.e. "A" (0 - sart; 1-end but excludes)
name.toUpperCase(); name.toLowerCase()

function getMilk() {
---your code here--
}
Math.pow(10, 2) // 10 to the power 2
Math.round(2.49) // => 2 and Math.round(2.5) // =>3
Math.random() //ex: (Math.ceil(Math.random() * 6)) to get a pseudo-random number for rolling a dice. It is called pseudo because it's a calculated value, not natural.
if (a === b) { // > or < or <= o >= etc. 
//block
} else {

}
Combine conditions using '&& or || '.
myArray = [item1, item2, item3] 
myArray.includes(item1) // this checks and return true/false
myArray.push(item) // pushes the item at the end
while(number <= 100) { > //here the code} // while loop checks the state/condition
for(var i=1, i<2, i++) {> //here the code} // for loop iterates
obj.addEventListener('click', function () {
// your code here. The addEventListener takes a string and a f-n as a parameter.
}) // This is synonym to below f-nality:

function add (num1, num2) {
  return num1 + num2;
}

function multiply (num1, num2) {
  return num1 * num2;
}

function calculator(num1, num2, operator) {
  return operator(num1, num2);
}
Note: the debugger; works well in chrome. We need to type 'debugger;' SHIFT + <ent> and then on the next line type ex: calculator(3, 4, multiply); <ent>. This should take to the debug mode.
*In a function or eventListener we can refer "this" method to find which element triggered the particular operation* Ex:

let keyElements = document.querySelectorAll('.drum');
for (let i=0; i < keyElements.length; i++){
  keyElements[i].addEventListener('click', function (){
    console.log(this); // sample output can be // <button class="w drum">w</button>
    } //and this.innerHTML can output 'w'. Based on this we can compare and use it.
*swtich statements*

switch(this.textContent) {
      case "w":
        var audio = new Audio('sounds/tom-1.mp3');
        audio.play();
        break;
      case "a":
        var audio = new Audio('sounds/tom-1.mp3');
        audio.play();
        break;
      }