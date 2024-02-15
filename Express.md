JS framework allows to create back-end. Although, we can accomplish many many tasks using node, Express specializes on backend web development. It's just like an electric screw driver. However, Express will use node internally to get the things done for us. 
*Creating and Express Server*
1. Create directory
2. Create index.js file
3. Initialize NPM (npm init -y, where -y doesn't ask interactive questions)
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
6. Start server (node index.js) {you can check it through ex: http://localhost:3000}
*hint: to check which ports are currently listening in a computer
netstat -ano |findstr "LISTENING" or netstat -ano | grep LISTEN (in bash)*
GET - request resource
POST - Sending resource
PUT - Replace reserve
PATCH - replacement/repair of a particular item not working instead of PUT, which replaces all
DELETE
*Basic GET
app.get('/', (req, res) => {
  console.log(req); // This will output on the server, not on the client browser. We can use req.rawHeaders to get the key/value pairs
  res.send('Hello World'); // or res.send(`<h1>Hello World</h1>`);
});
*After each change, we need to restart the server. Instead we can use nodemon, a tool auto restarts the node apps when a file change occurs *
So, instead of 'node index.js' use 'nodemon index.js'. For that, install 
*npm i -g nodemon* // -g to install globally
Targeting Endpoints using '/Endpoint'

To test the end points, we use Postman coz the GET responses are only usually visible in a browser.
*__Express Middleware__*
Before we send results to the requests, there could be multiple processes carried out in the middle such as a) login, authorize, b) preparing the date before processing, c) verifying the requester, identifying the status of the request, d) error handling, etc.
- a commonly used middleware is "Body Parser". This belongs to the category b) above. This is used mostly in html forms. Ex:
-   <form action="/login" method="post">
    <label for="email">Email</label>
    <input type="email" name="email" required>
    <label for="password">Password</label>
    <input type="password" name="password" required>
    <input type="submit" value="Submit">
  </form>
*We put above form html file or thing which not going to be changed, and also exposed to the public in a separate folder ex: 'public'*
Now, if we wanna send a file as response to a client's request, we can use 'res.sendFile()' method, which requires an exact path or an absolute path.
const app = express();
app.get("/", (req, res) => {
  res.sendFile(__dirname + "/public/index.html");
});
app.use()__ function allows you to add new middleware to your Express app.
app.use((req, res, next) => {
//here your middleware relevant code
next() // this to call next middleware
})
*install body parser*
*__ and then use app.post("/submit", (req, res) => () {}) to handle the post request through app.use(bodyParser.urlencoded({ extended: true }));*
Basically, anything put through the form (any number of key/value pairs, will be sent in the body as an object)
Commonly used logging middleware is 'morgan', which is an HTTP req logger for Node.
=> Next module Logger