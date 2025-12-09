It's a JS framework (built on top of node) allows to create back-end apps with little codes compare to node scripts alone. Although, we can accomplish many tasks using node only, Express specializes on backend web development. It's just like an electric screw driver. However, Express will use node internally to get the things done for us. 

##### 6 Steps Creating an Express Server
1. Create directory
2. Create index.js file
3. Initialize NPM (**npm init -y**, where -y doesn't ask interactive questions)
4. Install Express pkg (npm i express) {make sure to add "type": "module", in package.json file}
5. Write svr app in index.js
	ex initial code within bracket: {
		import express from "express"
	const app = express();
	const port = 3000;
	app.listen(port, () => {
	  console.log(`Server running on port ${port}`);
	});
	}
6. Start server by typing 'node index.js' {you can check it through ex: http://localhost:3000}
*hint: to check which ports are currently listening in a computer
netstat -ano | findstr "LISTENING" or netstat -ano | grep LISTEN (in bash)*
###### HTTP Requests
GET - request resource from a server
POST - Sending resource
PUT - Replace resource
PATCH - replacement/repair of a particular item not working instead of PUT, which replaces fully
DELETE

*Basic GET
app.get('/', (req, res) => {
  console.log(req); // This will output on the server, not client browser. We can use req.rawHeaders to get the key/value pairs
  res.send('Hello World'); // **or** res.send(`<h1>Hello World</h1>`);
});
*After each change, we need to restart the server. Instead we can use ***nodemon***, a *tool auto restarts the node apps* when a file change occurs *
So, instead of 'node index.js' use 'nodemon index.js'. For that, install 
*npm i -**g** nodemon* // -g to install globally
Targeting Endpoints using '/Endpoint'

To test the end points, we use **Postman** coz a browser can show direct responses received from the GET method, so other methods, such as POST, PUT etc doesn't involve directly on the browser, but on the back end, and the only thing received could be a status code.
Sample code for PUT below:
app.put("/user/abdul", (req, res) => {
  res.sendStatus(200);
}); //this put doesn't do anything except sending the OK (200), which can be tested in Postman.
*__Express Middleware__*
Before we send results to the requests, there could be multiple processes carried out in the middle such as a) login, authorize, b) preparing the data before processing, c) verifying the requester, identifying the status of the request, d) error handling, etc.
- a commonly used middleware is "**Body Parser**". This belongs to the category 'b)' above. This is used mostly in html forms, and has 'req.body' propertyEx:
-   <form action="/login" method="post"> //the 'action' has the route method*/
    <label for="email">Email</label>
    <input type="email" name="email" required> //'required' attribute enforces to fill that field for the users before clicking in the 'submit' button.
    <label for="password">Password</label>
    <input type="password" name="password" required>
    <input type="submit" value="Submit">
  </form>
*We 've put above html form file (or any file which not going to be changed meaning static files such as html, img etc, especially they are exposed) to public folder*
Now, if we wanna send a file as response to a client's request, we can use 'res.sendFile()' method, which requires an exact path or an absolute path or domain path. Ex:
import express from "express";
import { dirname } from "path"; //`path.dirname()` method returns the directory name of a `path`
import { fileURLToPath } from "url"; //Returns: fully-resolved platform-specific Node.js file path
==the res.sendFile below helps to render the index.html file to the browser. Therefore, we need to provide exact path instead of relative paths as done previously. That's why "path" and "url" modules are imported above.==
const __dirname = dirname(fileURLToPath(import.meta.url));
const app = express();
app.get("/", (req, res) => {
  res.sendFile(__dirname__ + "/public/index.html"); //consider the 'underscore' placed before dirname only.
});
**app.use()** function allows you **to add new middleware** to your Express app. And these middlewares gets triggered before we get to the app.get handler or similar.
app.use((req, res, next) => {
//here your middleware relevant code
next() // this to call next middleware
})
*install body parser \[import bodyParser from "body-parser]*
*__ and then use app.post("/submit", (req, res) => () {}) to handle the post request through app.use(bodyParser.urlencoded({ extended: true }));*
Basically, anything put through the form (any number of key/value pairs, will be sent in the body as an object, which can be retrieved through req.body. If bodyParser not in place, then it will throw undefined). So, with the bodyParser, we can get the form body content with 'console.log(req.body) or console.log(req.body.name, req.body.phone) etc'.

You can also include static folders as below:
`app.use(express.static("public"));`

Commonly used logging middleware is 'morgan', which is used to log requests coming from our server (an HTTP req logger for Node).
Ex: app.use(morgan("common")); / app.use(morgan("combined")); / app.use(morgan("tiny"))
https://betterprogramming.pub/should-i-use-promises-or-async-await-126ab5c98789
=> Next module Logger
A sample middleware is created below: 
app.use((req, res, next) => {
	console.log("Request method: ", req.method);
	next(); //here the next f-n determines, when we shld move on from this call. So order of the middleware is important.
})

function logger(req, res, next) {
  console.log("Request method: ", req.method);
  console.log("Request URL: ", req.url);
  next();
}
app.use(logger); // in this ex., instead of writing all the code within app.use() as in previous ex., a separate f-n is created first, then it is called.
*res.redirect("/");* - simply goes back to the main page.
==note that body-parser has become part of express. So, it's not required to import separately. So, we can write as below:==
app.use(express.urlencoded({ extended: true})); instead.