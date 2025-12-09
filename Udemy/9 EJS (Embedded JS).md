EJS help to write a little JS code within an HTML file. 
*Install EJS Language support in VSC*
*Then install `npm i express ejs`* //both 'express and ejs' pkgs will be installed.
It''s a template, which enables to send object with key/value pairs.

Of course, we can use res.send(`<h1>Hello</h1>`) But, this can be good for a simple .html file to be written. If we need a complex .html with other css etc separated, we need to use EJS. Similarly, the res.sendFile("index.html") is for static files, where we don't need to pass any key/value pairs or other information.
==place index.ejs file in "views" folder. And, note that, calling index.ejs from res.render() doesn't require it's views path==
EJS allows to dynamically create html files based on the input received from server side. This can be rendered using ***res.render()***:
'res.render("index.ejs", {name: req.body["name"]});  So, 'index.ejs' is rendered and 'name' is passed as key/value pair i.e. it must be an object with {}.
`<body> <h1> Hello <%= name %> </h1> </body>>` <= sample 'index.ejs' file.
Before using it install `EJS language support` plugin (Extension) to VSCode. Then you can create 'index.ejs' file.
*.ejs file is similar to the .html file. So, type ! + tab to make the html boiler plate and then follow up with all other things in it.*
`<body>
	<ul>
		<% for(let i=0; i<items.length; i++) { %>}
			<li>
				<%= items[i] %>
			</li>
		<% } %>
	</ul>
</body>`
#### EJS Tags
`<%= variable %> - here variable will be a JS output`
`<% console.log('hi') %> - within this we can execute any JS. Note, this console.log still gives the log in the main (node's) console.`
`<%- HTML Code %> - here we can send/render an html code (place them in " or ' quote. <%- "<h2>Heading 2</h2>" %>`
`<%%  %%> - this treated as escape seq, and whatever in btwn will be shown on html as it is`
`<%# This is an EJS comment %>`
`<%- include("headers.ejs") %> - this to include another .ejs file into d current .ejs. Ex: if we want to have header or footer`

__Passing data (Server <=> Client)__
Passing data from Server to Client is mentioned above through res.render() in the index.js and then retrieving in index.ejs using EJS Tags `<%= title %>` etc. 
`res.render("index.ejs", { name: message });`
However, index.ejs or EJS don't have the ability to check if the passed variable has some data or undefined or due to a bug nothing got passed. In this case the app can get crashed, when we try to use the data in 'ejs' file. So, use 'locals' preceded to the variables. It is a way to access all the vars sent over res.render(). We can also manually set it, ex: `res.locals = {data: 42}`and this local var can be accessed in the .ejs file. This locals var always exist, and can be used to check the existence of vars passed to .ejs and if it exists then we can use it normally. You can check using if statement. Eg. `if (locals.message) {}` this will check if message exists or not. 'message is what we try to send from index.js via res.render()'.
###### On the other hand, if we wanna pass data from .ejs to the server .js:
we can simply render the same .ejs file, ex. to send a POST data to the server and process it in the server, then display the results back on the client browser with the processed data. However, if the same .ejs file is used for both cases, we need to use __locals prefix__ to the variables in the .ejs file. See ex .ejs file: below:
<% console.log('from ejs ' + locals.numOfLetters) %>
    <% if (locals.numOfLetters) { %>
`      <h1>Your name has <%= locals.numOfLetters %> chars</h1>`
      <% } else { %> //probably we can avoid the 'locals.' in h1
        `<h1>Enter your name and hit Ok</h1>`
        <% } %>
          `<form action="/submit" method="POST">`
`            <input type="text" name="fName" placeholder="First name">`
`            <input type="text" name="lName" placeholder="Last name">`
`            <input type="submit" value="OK">`
          `</form>```
 And the corresponding index.js below:
`app.get("/", (req, res) => {
  `res.render("index.ejs");
`});
`app.post("/submit", (req, res) => {
  `let numOfLetters = countChars(req.body);
  `res.render("index.ejs", { numOfLetters: numOfLetters });
`});
## Partials using EJS
The CSS, images, HTML files what we 've used in Front End are static files and they cannot be simply added in the __header__ section of the .ejs file  as done in normal .html file. To use those __static__ files we need to use:
`app.use(express.static("public"));` and place all static files into that folder, then express will treat everything in 'public', as static. ex: the "href", and all paths will be relative to the 'public' folder in the style sheets. 
However, if we have multiple dynamic webpages, where we want to use same styles, images or other static files, we can use header.ejs or footer.ejs files to have one location to point to those static files instead of adding the same into all dynamic .ejs files. 
`<%- include("header.ejs") %>` //make sure to add the header at d beginning, footer at d end.
*To get the whole object or array for further processing, use JSON methods. Ex: below*
`  <script>`
      `var blogPost = '<%- JSON.stringify(blog) %>';`
      `console.log("test", blogPost);`
    `</script>`
    `above the blogPost object can be used in the normal JS file using JSON.parse(blogPost)`
    
###### If for some reason, the views folder is not visible, do the following: 
```
import { dirname } from 'path';
import { fileURLToPath } from 'url';
const __dirname = dirname(fileURLToPath(import.meta.url));
app.set("views", path.join(__dirname + "/views"));
```
```
***Getting an array into script***
<script>
let myArray = '<%- JSON.stringify(countries) %>'
myArray = JSON.parse(myArray);
myArray.forEach(element => {
console.log(element["country_code"]);
document.getElementById(element["country_code"]).style.fill = 'teal';
});
</script>
```