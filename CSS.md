Inline style: <h1 style="color: blue;">Style Me in Blue!</h1>
Internal style: target this within head section: <title>Internal</title>
  <style>
    h1 { // here h1 is the selector where the color is applied to
      color: red;
    }
  </style>
  External style: target this within head section <link rel="stylesheet" href="./style.css">
  Note: if we want to target an id use  ex: #main (if main is the id value).
  Targeting property and value ex: <p draggable="false">Draggable text as false</p>
  p[draggable="true"] {
  color: aqua;
*{ } - a universal selector
colorhunt.co - for more color selections or csfieldguide.org.nz/en for more visual selection of colors for different rgbs

Font Size: 1px = 1/96inch; 1pt = 1/72 inch (this is used for actual font-size ex: in word or similar); 1em = 100% of parent i.e. taken the m (widest letters full width); For ex: if <h1> is in the <body> and the <body> has 20px font, then if we say h1 {font-size: 2em}, it will have 40px for h1 font-size.
1rem = 100% of the root, meaning the root value is from the html default size. So, best to use rem instead of em. 

border: 10px solid black; // an ex: to define all in one
border-top: 0px; makes above border to take effect. 
text-transform: uppercase; // for text to uppercase
specificity for below element is in increase order: 
<li id="first-id" class="first-class" draggable>
li {color: blue;}
.first-class {color: red;}
li[draggable] {color: purple;}
#first-id {color: orange;}
Targeting an element within another element without giving a separate id or class:
<div class="box inner-box">
        <p class="white-text">White Text</p>
</div>
.inner-box p { //this looks first the class and then the targeted element within that class element
color: white;
}
Another way of targeting selectors is grouping. Ex .list, .menu {} two classes will have common properties and values. We can group ids, elements classes etc.
Another way is to target the child element: selector > selector {} //using the > symbol
Note: when grouping the type of selectors can be different. 
Another way to target is to use chain selectors (in btwn no space): selectorselector {}

Positioning
A. Static - this is the default position adding element one after the other
B. Relative - this will be relative to the supposed location i.e. static position
C. Absolute - relative to nearest positioned ancestor or top left corner of the webpage if none
D. Fixed - relative to top left corner of browser window. This is visible if we scroll down only. 
lascarides.github.io/fussyflags/ - check this if you want to practice some challenges in positioning

CSS Float - allows to wrap text around
ex: img { float: left;} // this makes the image to be left and text around it. footer {clear: left/right/both;}

Responsive Web sites in term of the narrowness of the devices such as mobile phone, ipad, notebook etc. can be achieved through:
1. Media Queries -     @media (max-width: 600px) { //max-width: 600px becomes the breakpoint to execute the CSS for this media classifier.
      /* CSS for screens below or equal to 600px wide ex: h1 {font-size: 15px; }*/
    }
    @media (min-width: 600px) and (max-width: 900) { /* apply styles*/}
1. CSS Grid
2. CSS Flexbox
3. External Frameworks ex: Bootstrap

**Flexbox**
declare using "display: flex". This makes most of the default properties ignored within that container. Ex: a div or p is a block element, and span, img are inline element. When these are placed within flex, they all will be treated as inline element, but those values can be changed.
So, by default the flex container will behave as a block. Instead we can specify
display: inline-flex // this will make it inline allowing other elements to be on the side. 
Flexbox's main axis depends on the direction it's set. Ex: if the flex-direction: row then the main axis is horizontal. In this case if we set flex-basis: 100px, each container inside will take 100px width. Otherwise, if flex-direction: column then the main axis becomes vertical. If we set flex-basis: 100px then it will take the height of the container to be 100px. 
https://css-tricks.com/snippets/css/a-guide-to-flexbox/
**Flexbox Sizing**
flexbox sizing follows this rule => Content width < width < flex-basis < min-width/max-width
->Meaning: if flex-basis is set, it will ignore the width setting if any. 
Default behaviour is flex-basis: auto; flex-grow: 0; flex-shrink: 1;
short hand format of writing above default behaviour is flex: 0 1 auto
However, the shortcut flex:1 == flex: 1 1 0 (i.e. grow 1, shrink 1, flex-basis 0, where flex-basis 0 will treat each item equally instead of auto, which looks at the content and grows accordingly)

GRID - we use this if we have 2 dimensional layout unlike Flexbox, which is single dimension (row/column) ex: declaration:
    .container {
      display: grid;
      grid-template-columns: repeat(8, 100px); //makes fixed width
      grid-template-rows: repeat(8, 100px); //makes fixed height
    } // instead of fixed w/h, we can use fr units such as 1fr, 2fr etc
    grid-template-columns: 1fr 400px minmax(200px, 500px); // 3 columns
    grid-auto-rows: 300px; // this will be used if we don't define enough rows and columns and another div/element is added then it will take the height of 300px. 
    grid-template-columns: auto 400px minmax(200px, 500px);
    rows and cols combined together are called tracks or we use term as row tracks or col tracks.
If four `<grid-line>` values are specified, `grid-row-start` is set to the first value, `grid-column-start` is set to the second value, `grid-row-end` is set to the third value, and `grid-column-end` is set to the fourth value
ex: grid-area: 2 / 1 / 2 / 4; or you can set individually as: 
grid-column: 1;
grid-row: 2; // to fill the cells we can use as below:
grid-column: 2 / span 4;
grid-row: 1 / span 5;