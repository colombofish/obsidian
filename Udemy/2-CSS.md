###### Inline style: <h1 style="color: blue;">Style Me in Blue!</h1>
or <html style="background: red;"><body><h2 style="color: green">Testing the background</h2></body></html>
Inline CSS can be used if only targeting a single element of a page. But, best is the external style sheet. 
###### Internal style: 
target this within head section: <!-- <title>Internal</title> -->
<!--style-->
    h1 {  /*here h1 is the **selector** where the color (the property) and red (the value) is applied to.*/
      color: red;
    }
  <!--/style-->
/*here h1 is called element-selector, bcoz it is targeted on a particular element*/
/*also, we can have **class selector** ex: '.red-text' or an **id-selector** ex: '#main' or **attribute-selector**, which can be applied if any element meets the attribute criteria mentioned in the style-sheet*/
example for attribute selector below:
p[draggable] { color: blue } or p[draggable="false"] { color: red } /*css*/
<p draggable="true">Drag me </p>
<p draggable="false">Don't drag me </p>
/*Note: the class-selector can be applied to many elements on a web-page, but the id-selector should be applied to one element per page*/
  External style: target this within head section <!--link rel="stylesheet" href="./style.css"-->
  Note: if we want to target an id use for ex: #"main" (if main is the id value).
  Targeting 'property & value' ex: <!--p draggable="false"-->Draggable text as false<\/p>
  p[draggable="true"] {
  color: aqua;

"* { }" - a universal selector <!-- *Note that * is there in front as a universal selector as in a wild card -->
https://colorhunt.co - for more color selections or csfieldguide.org.nz/en for more visual selection of colors for different rgbs

Font Size: 1px = 1/96inch; 1pt = 1/72 inch this is used for actual font-size ex: in word the point is used for the font size. 
1em parent i.e. taken the m (widest letters full width); For ex: if **h1** is in the **body** and the **body** has 20px font, then if we say h1 /*font-size: 2em*/, it will have 40px for h1 font size.
1rem = 100% of the root, meaning the root value is from the html default size. So, best to use rem instead of em, because of the fixed value expected from the root (html) font-size set instead of an element's parent font-size as in 1em. 
For font-family (type of fonts), use always an alternative generic font as backup
ex: h2 {
	font-family: "Times New Roman", serif /*Note the "" as we cannot have spaces for the font as in Windows*/
}

For varieties of fonts => https://fonts.google.com; Here, select whatever the font types, I need including the sizes if there are many, then Get it and copy the code when the 'link' is selected. Include it in the html head section just below closing the head. Google also provides a sample CSS to use, which can be placed within 'style section'. After renaming the classes according to Google's instruction, and applying those fonts to the elements, you should see the results. Of course, you can also apply them directly to the elements, without specifying a class. Check for 'WebDev-Sep2025\6.1FontProperties\index.html' for example.
**CSS inspection** - 3 dots -> More Tools -> Developer tools in Chrome browser. Under Elements -> Styles, we can modify/add some styles without affecting the original. On top of this, if you click on the 3x dots within the developer tool (not the browser 3x dots), then More Tools, you find CSS Overview, where you can get more info about the color combination used, fonts used etc. 

border: 10px solid black; // an ex: to define all in one, where 10px is the thickness
// note that the border thickness goes outward rather than inward
border-top: 0px; makes top border to be none. 
border-width: 0 10px 20px 30px (taken from top to left clockwise, and similarly padding & margin)
Padding: this is the space btwn border and the element
margin: is taken between two elements from it's border. 
text-transform: uppercase; // to make the text to uppercase

*==To separate or group elements together, we can use "DIV" element, and add all elements, which need to be treated as one group
Hint: You horizontally center a div by giving it a width of 50% and a margin-left of 25%.
Hint: Set the image to have a width of 100% so it fills the div.==*
### CSS Cascade
The cascade decides which rule will get applied to the specific element. 
External style sheet -> internal style sheet i.e. higher priority is for inline applied for an element. There are 4 categories looked into to decide the priority of cascading: 
1. Position, 
ex: if there are 2 rules for the same element the last rule gets applied. 
2. Specificity,
specificity for below element is in increase order: 
<!--li id="first-id" class="first-class" draggable-->
li {color: blue;} <!-- element selector is the least specific in this example -->
.first-class {color: red;} <!-- class selector, next more specific-->
li[draggable] {color: purple;} <!-- attribute selector. Suppose we have an element got multiple attributes, where we can style based on its attribute. Another ex. of an attribute can be 'src'-->
#first-id {color: orange;} <!-- #id selector, final level the most specific -->

3. Type (i.e. external; internal; inline style (css code) where inline has highest priority)
4. Importance. Here if "!important" keyword is added after the property, that will have the highest priority. See the last ex. in the image. 
![[Pasted image 20240810124907.png]]

###### Combining CSS Selectors:
**i.e.** Targeting an element within another element without giving a separate id or class
<!--div class="box inner-box">
        <p class="white-text">White Text</p>
</div-->
.inner-box p { //this looks first the class and then the targeted element within that class element
color: white;
}
Another way of targeting selectors is **grouping**. Ex .list, .menu {} of two classes to have common properties and values. We can group ids, elements classes etc. ex: h1, h2 { color: blue;}
**Note:** when grouping, the type of selectors can be different, such as class, id, element etc. using the 'comma'. 
Another way is to **target the child element**: selector > selector {} //using the > symbol. Here the second selector becomes direct child of the first selector, the parent. 
Another way is to **target it's descendants with a space**. Here, the rule will apply to all levels deep.
Another way to **target using chain selectors** (in btwn no space): selectorselector {}
ex: h1#title.big.business *here we have a h1 with an id=title, class="big business" i.e. 2 classes*. This way, we target the element more specifically. 
Note: if there is an element such as h1 in above example, that need to be placed first. 

###### Positioning
A. Static - this is the default positioning adding element one after the other. Hence we don't need to set this -> position: static;
B. Relative - this will be relative position to the original position (or supposed position, which in general is the static position), and moved from the location where it should be with the keywords ex: left: 50px; top: 50px;. Note the keywords **left, and top**.
C. Absolute - relative to nearest positioned ancestor or top left corner of the webpage if no ancestor. Nearest positioned ancestor meaning, it is positioned in relation to the direct parent. So it's absolute position will be relative to its relative ancestor. If there is no relative ancestor, then it will be positioned to the top left corner of webpage. 
D. Fixed - relative to top left corner of the browser window. Even if we scroll down, the position will be fixed. 
lascarides.github.io/fussyflags/ - check this if you want to practice some challenges in positioning

**Z-Index** which determines which element is going to sit on top of another. Ex: if A has Z index 100, B has 50, then A will be on top of B. Default is 0. In this case, to set it to get behind we can provide "z-index: -1";

##### Aligning elements
**CSS display: inline/block/inline-block;**
Based on the 'display' property value, an element will be fit into the same line or separate line. 
**Note***: if an element is set as 'inline', then it's width and height will depend on it's content only. We can't set them separately. 
However the **inline-block** value allows us to set the width & height as well, and enable us to put on the same line. 
By default, most of the elements have the display property value set to 'block'. However, if we set it to 'inline', they will occupy only the required space in a line. /*ex: h2 { display: inline }*/
==ex: a 'div' element is a block element. If you set the 'display: inline-block', it will make them as separate blocks and place it on the same line as long as the space allows. If you set it as 'display: inline' then it will put the div blocks together attached. You will not see them as separate blocks, and it will appear as one single block although they are two ==
==On the other hand, you can set the height and width for an 'inline-block', but you can't set width/height for 'inline'. 
{display:none} makes the particular element or block to disappear==
**CSS Float** - allows to wrap text around an image.
ex: img { float: left;} // this makes the image to be left and the text to wrap around it. However, if we want the footer to be not included in case we don't have enough text, which wraps around, we need to clear it using {clear: left/right/both;}

**Responsive Web sites** in term of the width of the devices' display such as mobile phone, ipad, notebook etc., web pages need to be responsive. This can be achieved through:
1. Media Queries -     @media (max-width: 600px) { //max-width: 600px becomes the breakpoint to execute the CSS for this media classifier.
      /* CSS for screens below or equal to 600px wide ex: h1 {font-size: 15px; }*/
    }
    @media (min-width: 600px) and (max-width: 900px) {  /* apply styles} or
    @media (550px <= width <= 595px) {} or
    @media screen(orientation: landscape) {} as a general practice this screen or print is not used often */
2. CSS Grid    Ex. style of a div container 
	.grid-container {
      display: grid;
      grid-template-columns: 1fr 1fr; /* 2 columns */
      grid-template-rows: 100px 200px 200px; /* 3 rows */
      gap: 30px; /* gap between the 'div's */
    }
    .first {
	    grid-column: span 2; [this means it takes both columns defined above]
    }
    .card { background-color: blue}
   <!-- Above CSS can be applied for the below <body> content.
    <div class="grid-container">
		<div class="first card"></div>
		<div class="card"></div>
		<div class="card"></div>
		<div class="card"></div>
		<div class="card"></div>
   </div> -->
   
==CSS GRID is best to use for Two Dimensional layout.==

1. CSS Flexbox (This is for Single dimensional layout). 
![[Pasted image 20250927155817.png]]
2. External Frameworks ex: Bootstrap

**Flexbox**
declare using "**display: flex**" . This makes most of the default properties ignored within that container. Ex: a div or p is a block element, and span, img are inline element. When these are placed within flex, they all will be treated as inline element, but those values can be changed.
![[Pasted image 20251003120422.png]]
So, by default the flex container will behave as a block. Instead we can specify
**display: inline-flex** // this will make it inline allowing other elements to be on the side. This is similar to inline-block display property.
![[Pasted image 20251003120605.png]]
Flexbox's main axis depends on the direction it's set. Ex: ***if*** the ***flex-direction: row*** then the ***main axis*** is ***horizontal*** and the cross-axis is vertical. In this case if we set ***flex-basis: 100px***, each container inside will take 100px width. Otherwise, ***if flex-direction: column*** then the ***main axis*** becomes ***vertical***. If we set flex-basis: 100px then it will take the height of the container to be 100px. But **remember**, that flex-basis can be only applied to the child element, not in the main/parent container. 
**order** property: suppose we have 5 items in a flexbox, if we want to arrange the items in a different order, then we need to use the 'order: 1 or more number', because by default each item will have set as order: 0; 
**flex-wrap: wrap** property: suppose we have a row based flex-box and we run out of space in the row, then it will take the items to the next row (if the flex-direction: row). By default, this is set as "flex-wrap: nowrap". Similarly, if the flex-direction: column, the items will go to next column. 

https://css-tricks.com/snippets/css/a-guide-to-flexbox/
![[Pasted image 20240816073637.png]]

**Flexbox Sizing**
flexbox sizing follows this rule => Content width (when nothing is set) < width (if set to container or items) < flex-basis < min-width/max-width
->Meaning: if flex-basis is set, it will ignore the width setting if any or Content width. Similarly min/max width has higher priority, so it will ignore other settings on the left above. Ex: if flex-basis and width of an item is set for it, the flex-basis take priority. However, an item can only shrink up to its minimal required size, such as the longest word in a paragraph. 
Default behavior is flex-grow: 0; flex-shrink: 1; flex-basis: auto; This auto checks the content of each item in the flex-box, and sets it's width accordingly. If we want equal width for each content, then set flex-basis:0; instead. Note, that the minimum width will be decided based on the size of the longest word within a paragraph. 
short hand format 'flex' covers 0 1 auto for grow, shrink, flex-basis
However, the ***shortcut*** flex:1 == flex: 1 1 0 (i.e. grow 1, shrink 1, flex-basis 0, where flex-basis 0 will treat each item equally instead of auto, which looks at the content and grows accordingly)
**Note**, ***height: 100vh*** would represent ***100% of the viewport's height*, *or the full height of the screen.*** And of course, VW stands for “viewport width”, which is the viewable screen's width. 100VW would represent 100% of the viewport's width, or the full width of the screen.
/*for the items to be aligned within a container, use "align-self: value" to the items, not to the parent container. Also, try with "nowrap" property to the container.*/
/*similarly, align-content property for the container works when the flex-wrap property is set to wrap.*/
/*sometimes it's worth trying to add text-align: center to make the content of a div to be centered.*/
**GRID** - we use this if we have 2D layout (like table structure, rows & columns) unlike Flexbox, which is a single dimension layout (row or column). Ex. declaration of a grid:
    .container {
      display: grid;
      ***grid-template-columns***: repeat(8, 100px); //makes 8x fixed width or type 8x 100px w/o space
      ***grid-template-rows***: repeat(8, 100px); //makes 8x fixed height
      gap: 10px;
      width: 800px //this width can be set if our grid contains extra spaces if we define col/row width somewhere else, such as to those particular div s using class or other instead of directly adding the width in the template-rows/columns as above. 
    } 
Instead of defining grid-template-rows, grid-template-columns separately, we can use as below:
/**grid-template**: 100px 200px / 100px 200px; (for 2 rows & 2 columns)./
    /*by using fixed width for rows and columns, we can't expect the webpage to be responsive, so*/
    // instead of fixed w/h, we can use fr units such as 1fr, 2fr etc for responsiveness
    grid-template-columns: 1fr 400px minmax(200px, 500px); // here the 3rd col's min-width will be 200px, and max-width will be 500px.
    ***grid-auto-rows***: 300px; // this property can used when we don't have enough rows and columns defined, then when another div/element is added, then it will take the height of 300px. 
    /*Note: continuing with above note, if we have more items than the grids defined by rows & columns, the additional items will be set to auto mode, meaning they will occupy the defined column size, but the row size will be decided by the content.*/
    grid-template-columns: ***auto*** 400px minmax(200px, 500px); // <= gives some responsiveness. 
    rows and cols combined together are called ***tracks*** or we use term as row-tracks or col-tracks. Within the intersection of tracks we find 'cells' as the smallest unit in a 'grid'.
So, we can use multiple cells to create a grid-item.
grid-column: span 2; meaning the item starts from the position where it supposed to start, but takes 2 grid columns space for this particular item. 
Note: if you look through the Chrome dev tool, we can expand the grid-column > property, which would show grid-column-start & grid-column-end. /*just click on the 'grid' icon by the container div (elements tab)*/

If four `<grid-line>` values are specified then, `grid-row-start` is set to the first value, `grid-column-start` is set to the second value, `grid-row-end` is set to the third value, and `grid-column-end` is set to the fourth value
ex: grid-area: 2 / 1 / 2 / 4; or you can set individually as: 
grid-column: 1;
grid-row: 2; // to fill the cells we can use as below:
grid-column: 2 / span 4; (try grid-column: 2 / 6 for span 4)
grid-row: 1 / span 5;
or 
grid-column: span 2; /*this specifies the number of cells occupied by column will be 2, from the current position*/
==Note: the numbers above starts from 1 from left handside, and starts from -1 from the right handside, which is the end of the line.==

Similar to Flex, Grid items also can be set order, where 0 is default, which is the highest if positive numbers. 

==Unlike flex, grid can be positioned to overlap with other item.== 
/*exampleN
#garden {
  display: grid;
  grid-template-columns: 20% 20% 20% 20% 20%;
  grid-template-rows: 20% 20% 20% 20% 20%;
}*/
.a { /*assigning a background image for a button with a class of 'a'*/
  background-image: url('./images/tom2.png');
}