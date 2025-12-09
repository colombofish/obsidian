# Seems to be obsolete. So forget it. 
JScript is the most popular library, introduced to reduce the length of coding.
Attach the CDN link from jquery.com/download to the main page (copy the script fragment).
ex: document.querySelector("h1") can be written using jQuery as 
jQuery("h1") or can be written as $("h1")
ex1: $("h1").css("color", "red"); // the same thing below, but with some error handling in case if the script didn't load yet. 
$(document).ready(function () { // this ensures
  $("h1").css("color", "red"); // here we select the css from js.
}); // we can avoid this error handling if we include the script before the eof /body element.
$("button")  - this selects the button/s independently on the number of buttons, unlike document.querySelector("button") for 1 and document.querySelectorAll("button") for many.
To get the value we can use 'console.log($("h1").css("font-size"))'
Note, that instead of including css properties inside the JS file, we can use addClass/removeClass etc. to keep the styles in the .css file. '$("h1").addClass("big-title");' or 
'$("h1").addClass("big-title margin-50");' // note 2 classes included/added here.
'$("h1").hasClass("big-title");' returns 'true' if it has.
to change text using jQuery:
1. $("h1").text("bye")