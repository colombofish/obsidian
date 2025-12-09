Node REPL (Read Eval Print Loop) - is a computer run-time env, where user inputs are read and evaluated, and then the results are returned to the user.
to initiate the node REPL, just type 'node' (this takes to the node's interactive mode) 
Now while being in the node prompt, if we type > 5+3 <\ent>, this will output the value 8, and then return to the cmd prompt. So, Read, Evaluate, Print, then Loop is shown in there. {.help, .exit - couple of cmd formats}. This node shell also works like programming env, so we can input like 'let c = 32; let a = 5; a +c => Results will be 37' etc., similar to JS console in a browser. 
Node is not a framework, but it's a Run Time Environment. 

This concept leads towards the fact that, we can run JS code by typing 'node inde.js', where node becomes the Run Time Env.

##### Native Node Modules
These are ready made tools available such as File browsing (locally or remote through web browsing), Networking to reach through internet for connectivity and back-end operations etc. For details or help, check nodejs.org/docs
We can use either CJS(Common JS) or EJS pattern. 
ex usage of: fs.writeFile
const fs = require("node:fs")
fs.writeFile('message.txt', 'write this msg into the file', (err) => {
if (err) throw err;
console.log('File has been saved');
})
==Note: with JS, reading/writing to a file may be a disaster by allowing someone who browses the Internet, having access to your local FS (File system). But in the case of node, which is run locally we can allow to do the local operations such as R/W file etc.==

or Read as below:
fs.readFile('text.txt', 'utf8', (err, data) => { // if not 'utf8' meaning string format given, the output will be in raw format
  if (err) throw err;
  console.log(data);
});
##### Node Package Manager - npm
This is an open source code library, which is bundled along with node. That means, the Native Node Module have limited resources or pkgs in there, but npm is a collection of libraries coming from every part of the world. So, if we have node installed, we will have npm also installed to retrieve and use pkgs. 
We can initialize a project while being in the project folder with cmd '***npm init***'. This will help creating the config file, which is 'package.json'. {'**npm init -y**'-to say yes for all questions, so that it doesn't prompt further} 

Next, we can install an npm pkg using 'install i' cmd, where 'i' is short for install. We can find the pkgs in https://npmjs.com
ex1: 'npm install sillyname' / npm i pkg1 pkg2 pk3 etc. (if we wanna install multiple pkgs). This will add sillyname pkg to the "dependencies" property list in package.json
ex2: 'npm i' //this installs all dependencies found in package.json

*Above require is from the Common JS* (CJS), which is older way. 
From Node version 12 onwards, we can use ESM (Ecma Script Module), which uses 'import' keyword instead of 'require', which standardizes both front, and back-ends.
**To use ESM**, we need to **add** '"type": "module"', best after the "main" keyword in the package.json (conf. file). Then we can use import the objects and methods to our project. Syntax below
***import*** method/object(we wanna import) ***from*** "specify the pkg/module (which holds the those methods/objects)".
Tip: specify the "pkg/module" first, after that "method/object", so the intellisense will know to suggest the names.

Package library: https://www.npmjs.com/
==note: try not to mix things like 'import' and 'require' types of modules into the same project. Instead, if you are using module type, then use imprt for all modules instead of require==
Sample project: 
***Generating QR codes from any url***
Here we will use 2x pkgs. a) inquirer.js - this to get input from a user, b) qr-image - which generates images as png to save in our local folder.

=> Next module Express
=> Next module Logger
