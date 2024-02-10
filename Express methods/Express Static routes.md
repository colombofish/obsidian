import express from 'express'

const app = express();
const port = 3000;
const contact = `<strong>Address: </strong><br>
                  111, Cambridge Street, Luton <br>
                  + 44 7533312114`
  
app.get("/", (req, res) => {
  res.send("<h1>Hello World</h1>");
})
  
app.get("/contact", (req, res) => {
  res.send(contact);
})

app.post('/', (req, res) => {
  res.send('Got a POST req.');
})

app.put('/user', (req, res) => {
  console.log('Got a PUT req on /user');
})
app.delete('/user', (req, res) => {
  console.log('Received an anonymous /user delete');
})

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
})