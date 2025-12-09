There are different types of APIs. A few popular ones are `GraphQL, SOAP, REST:API, gRPC, etc.` are all different architectural styles. For Web dev. REST is most popular API, we interact with HTTP protocol. 
International Space Station (ISS) - https://wheretheiss.at/w/developer

[Bored API Documentation (appbrewery.com)](https://bored-api.appbrewery.com/) for learning purposes.
###### Query parameters
This usually for filtering based on the key/value pairs provided
GET https://bored-api.appbrewery.com/filter?type=education 'after an endpoint, provide '?query=value&query2=value'
###### Path parameters
https://bored-api.appbrewery.com/activity/3943506 where 3943506 is identified as the unique path parameter such as id or key.
*Once you get a response in JSON, we can use `jsonviewer.stack.hu` to view the structure. Otherwise, they can be in flat pack, and tracing relevant data may be time consuming*
[JSON Editor Online: edit JSON, format JSON, query JSON](https://jsoneditoronline.org/#left=local.xosadi)

Sample JSON object: 
{
    "activity": "Go to a concert with local artists with some friends",
    "availability": 0.3,
    "type": "social",
    "participants": 3,
    "price": 0.4,
    "accessibility": "Minor challenges",
    "duration": "hours",
    "kidFriendly": true,
    "link": "",
    "key": "2211716"
}
==Note:== JSON key(s) is(are) in "quotes", meaning it's a string, anyhow the value could be any such as number, arrays, string etc. However, the JScript object key is variable, we don't put that in "quotes". So, JSON is a flat pack of string, which is easy to send over the internet and convert to internal requirement. Therefore, we need to serialize the JS objects into JSON as below, and vice versa. 
##### JS Object to JSON object
const jsonData = JSON.stringify(data); //packs JS object into JSON data
const data = JSON.parse(jsonData); //unpacks JSON into JS object

Above API GET/POST requests were done using 3rd party tools such as Postman. For Server side (meaning our nodejs app side) requests, we can use Axios, instead of using native JS, which is a long method.
Note: in Axios, we don't need to use JSON.parse() to convert responses received in JSON to JS. 
###### Authentication requirement can be any of below:
0. No authentication - things could be limited based on the hit/min rate ex: 100hits /15min by checking the IP and tracking the \#of hits. These are usually avail for public APIs get methods. 
1. Basic authentication - authenticating ourself to the API provider through u/p. This is done by passing over Base64 Encoded string through the request header. Basically, after the Base64 encoding, the string which is sent represents a different chars than original. But, that can be reverse engineered if it is sent over plain http. Format username:password will be put in the authorization header in the request. [[Base64 Decode and Encode - Online](https://www.base64decode.org/)] Check https://secrets-api.appbrewery.com for practice.
2. API Key authorization - this similar to u/p. We don't use u/p, instead use the API Key either in the Header or can send as Query params depending on the requirement. Api key is more secure as we don's pass u/p. 
3. Token based authentication - this seems to be more secure. Once the user is logged in using u/p, a token will be generated, and then the token is used to interact with API methods. OAUTH is an industry std for token based authentication.
Authentication: This enables to identify who is the user (ex: through loggin in with u/p or by providing API Key). Howerver, 
Authorisation: Allows to use an API/resources according to the user hierarchy (if admin, then have total access). 
Although it is possible to crack the u/p sent via Basic Authentication (Base64), it is still used if it is https (cryptography used to secure the data sent over the internet). However, if the site is somewhat compromised, then u/p can be compromised too. Therefore Api key is more secure on this instance. 
The config related data can be passed as below:
Initially `npm install axios`, then:
`axios.get(URL, {
    headers: {
      Authorization: `Bearer <YOUR TOKEN HERE>`
    },
  });`or 
  const config = { headers: {
      Authorization: `Bearer <YOUR TOKEN HERE>`
    },};`
  axios.get(URL, config  });`
  *Check the code examples in '5.4 API Authentication'*
  For methods such as POST and PUT, we need to provide extra data, we can call it as body. Ex: if we wanna u/p from a form, we use POST method and attach the u/p in a body ex: { user: ${username}, pass: ${password}} etc. 
  The PUT request will hold all data, that we want to update or change the record in the back end. But, the PATCH can have partial update. 
  Note
 `Creating your own APIs`
 ```
 app.post("/post-secret", async (req, res) => {
  console.log(req.body);
  try {
    const resultPost = await axios.post(API_URL + "/secrets", req.body, config);
    console.log(resultPost.data);
    res.render("index.ejs", {content: JSON.stringify(resultPost.data)});
  } catch (error) {
    res.render("index.ejs", { content: JSON.stringify(error.response.data)});
  }
  // TODO 2: Use axios to POST the data from req.body to the secrets api servers.
});
 ```
***Note***: the `await` is from Promise, which waits for the axios.post() to get executed first before going to the next lines. 

**Rapid APIs** - a place where APIs accessible, or can make accessible for others on a paid basis. 
**REST APIs** - architecture (rules how API should be)
- What makes an API restful? A: 1. It makes a std http methods (get, post, put, patch, delete); 2. It should have a std data format (JSON, XML etc.) in response. This is the representation part sent to the client; 3. Clients and Servers in RESTFUL APIs are completely separate, and they are not in the same system or at least in the same file, and they able to message over the network req/res, and built separately. 4. Stateless-ness i.e. it should contain all information in the request to process the request. Meaning the server doesn't store any info from Client. 5. Next the REST API should be resource based, it is centered around resources and uses URI/URL to identify resources. URL is a particular address of a resource, and URL is a type of URI. 
Note: Current latest option is use `async` within the express HTTP request methods, and use `await` for each axios calls instead of old `.then` expressions. See below samples:
```
axios.get('/user?ID=12345')
  .then(function (response) {
    // handle success
    console.log(response);
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
  .finally(function () {
    // always executed
  });
```
```
app.get("/bearerToken", async (req, res) => {
  try {
    const config = { headers: {
      Authorization: `Bearer ${yourBearerToken}`
    },
  }
    const responseToken = await axios.get(`${API_URL}secrets/4`, config);
    console.log(responseToken.data);
    res.render("index.ejs", {content: JSON.stringify(responseToken.data)});
  } catch (error) {
    console.error("Failed to make request: ", error.message);
    res.render("index.ejs", {error: error.message});
  }
```
 *some readings - [What is ‘CORS’? What is it used for? | by Electra Chong | Medium](https://medium.com/@electra_chong/what-is-cors-what-is-it-used-for-308cafa4df1a)*
 https://github.com/appbrewery/public-api-lists
##### Internal APIs
ex: if working in a company, where we need to track inventory of internal things etc., and we can create those internal APIs to get the information from back end. Note, internal APIs may be not documented to public, but external parties could figure out based on the company profile, the possible endpoints. 

`res.json(jokes[index])` // to send response by converting the JS object to JSON format.
###### for path params
ex: localhost:3000/jokes/2;
`app.get(`/jokes/:id`, (req, res) => {'
  `const id = parseInt(req.params.id);`
  `res.json(jokes[id - 1]);`
`})` or use `const jokesFound = jokes.find((joke) => joke.id === id); res.json(jokesFound);`
```
//3. GET a jokes by filtering on the joke type

function capitalizeFirstLetter(text) {
  return text.charAt(0).toUpperCase() + (text.slice(1)).toLowerCase();
}

app.get("/filter", (req, res) => {
  let type = req.query.type;
  type = capitalizeFirstLetter(type);
  const jokesFromType = [];
  jokes.forEach((joke) => {
    if (joke.jokeType == type) {
      jokesFromType.push(joke);
    }
  });
  res.json(jokesFromType);
})
OR, instead of forEach callback f-n use below:
const filteredActivities = jokes.filter((joke) => joke.jokeType === type)
```