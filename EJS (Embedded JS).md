*Install EJS Language support in VSC*
*Then install 'npm i express ejs'* //both 'express and ejs' pkgs will be installed.
A template, which enables to send object with key/value pairs
*make sure to have installed ejs*
Of course, we can use res.send(<h1>Hello</h1>); But, this can be good for a simple .html file to be written. If we need a complex .html with other css etc separated, we need to use EJS. Similarly, the res.sendFile("index.html") is good for static files, where we don't need to pass any key/value pairs or other information.

For this we use 'res.render("index.ejs", {name: req.body["name"]}); and the index.ejs file may contain as below. Note above the 'index.ejs' is rendered and 'name' is passed.
`<body> <h1> Hello <%= name %> </h1> </body>>`

*.ejs file is similar to the .html file. So, with ! + tab to make the html boiler and then follow up with all other things in it.*

#### EJS Tags
`<%= variable %> - here variable will be a JS output`
`<% console.log('hi') %> - within this we can execute any JS`
`<%- HTML Code %> - here we can send/render an html code`
`<%%  %%> - this treated as escape seq, and whatever in btwn will be shown on html as it is`
`<%# This is a comment %>`
`<%- include("headers.ejs") %> - this to include another .ejs file into d current .ejs. Ex: if we want to have header or footer`
__Passing data (Server <=> Client)__
Passing data from Server to Client is mentioned above through res.render() in the index.js and then retrieving in index.ejs using EJS Tags `<%= title %>`. 
`res.render("index.ejs", { name: message });`
However, index.ejs or EJS don't have the ability to check if the passed variable has some data or undefined or nothing passed. In this case the app can get crashed. Therefore, we can use 'locals' preceded to the variables. It is a way to access all of the vars send over res.render(). We can also manually set `res.locals = {data: 42}`and this local var can be accessed in the .ejs file. This locals var always exist, and can be used to check the existence of vars passed to .ejs and if it exists then we can use it normally.

###### On the other hand, if we wanna pass data from .ejs to the server .js:
we can simply render the same .ejs file if we wanna send some POST data to the server, process in the server, and display on the client browser with the processed data. However, if the same .ejs file is used for both cases, we need to use __locals prefix__ to the variables in the .ejs file. See ex .ejs file: below:
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
The CSS, images, HTML files what we 've used in Front End are static files and they cannot be simply added in the __header__ section of the .ejs file. To use the __static__ files we need to use:
`app.use(express.static("public"));` and place all static files into that folder, then express will treat everything in 'public' as static. ex: the "href" will be relative to the 'public' folder in the style sheet. 
However, if we have multiple dynamic webpages, where we want to use same styles, images or other static files, we can use header.ejs or footer.ejs files to have one location to point to those static files instead of adding the same into all dynamic .ejs files. 
`<%- include("header.ejs") %>` make sure to add the header at d beginning, footer at d end.
*To get the whole object or array for further processing, use JSON methods. Ex: below*
`  <script>`
      `var blogPost = '<%- JSON.stringify(blog) %>';`
      `console.log("test", blogPost);`
    `</script>`
    `above the blogPost object can be used in the normal JS file using JSON.parse(blogPost)`
    