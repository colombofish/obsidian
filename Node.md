Node REPL (Read Eval Print Loop) - is a computer run-time env, where user inputs are read and evaluated, and then the results are returned to the user.
to initiate the node REPL, just type 'node' (this takes to the node's interactive mode)
Otherwise, we can run JS code by typing 'node inde.js'
*Native Node Modules*
There are ready made tools available such as File browsing (locally or remote through web browsing), Networking to reach through internet for connectivity and back-end operations etc. For details, check nodejs.org/docs
ex usage of: fs.writeFile
const fs = require("node:fs")
fs.writeFile('message.txt', 'write this msg into the file', (err) => {
if (err) throw err;
console.log('File has been saved');
})

or Read as below:
fs.readFile('text.txt', 'utf8', (err, data) => { // if not 'utf8' meaning string format given, the output will be in raw format
  if (err) throw err;
  console.log(data);
});
*Node Package Manager - npm*
npm is bundled along with node. So, we can initialize with 'node init' for the first time using 'npm init' to initialize the project. This will create the package.json the config file. Provide basic info such as pkg name, description etc. on the interactive cmd line. Next, we can install an npm pkg using 'install i' cmd, where i is short for install. We can find the pkgs in https://npmjs.com
ex: 'npm install sillyname'
*Above require is from the Common JS* (CJS)
From Node version 12 onwards, we can use ESM (Ecma Script Module), which uses 'import' keyword instead of 'require', which standardizes both front, back-ends.
To use ESM, we need to add '"type": "module"', best after the "main".. in the package.json
Package library: https://www.npmjs.com/

=> Next module Express
=> Next module Logger
