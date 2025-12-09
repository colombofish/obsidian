Postgres - An open source dB management system.
*install the node-postgres pkg through npm*
`npm install pg`
If locally, then install **Postgres server**, and **pgAdmin** (a UI to admin Postgres server)
https://sbp.enterprisedb.com/getfile.jsp?fileid=1258649 - to download client/server.
**user**: postgres (M[ullathi..]..1!)
port: 5432 (default)
```//First create the table structure (pgAdmin). Select query tool and type d following:
CREATE TABLE friends (
id SERIAL PRIMARY KEY,
name varchar(50), // CHAR(50) will occupy 50 chars, while VARCHAR won't if not max.
age INT, 
is_cool BOOLEAN
); // make sure to add the ';'.

// Next you can right-click on the table and import data, ex: from a .csv
// If you have any header in .csv, make sure to click on the header option.
// Make sure to match the column name as in the .csv
```

```
import Client from 'pg'; //or import pg from 'pg', and
const db = new Client({ //or add pg.Client()
	user: "postgres", 
	host: "localhost", 
	database: "world", 
	password: "Manadile1!", 
	port: 5433
});
db.connect();
db.query("SELECT * FROM capitals", (err, res) => {
	if (err) {
		console.log("Error executing query", err.stack);
	} else = {
		quiz = res.rows;
	}
	db.end();
});
```
**NB**: above Postgres specific '**SERIAL**' key increments the id auto, and we don't need to specify when inserting rows.
Another datatype is 'TEXT', which doesn't require to specify the number of chars, but will also occupy necessary space similar to varchar. And, in modern days TEXT is commonly used than varchar. As per studies, TEXT is bit slower compared to varchar, but it makes life easier not to re-design the length of field if needed.
**Read more on** https://postgresql.org/docs/current
``` *QUERY NOTES*
SELECT country, wheat FROM food WHERE rice > 100.0; or 
select rice from food where country = 'United States'; //note 'quote'
Other Comparison Symbols are: <, >, <>, >=, <=
SELECT country FROM food WHERE country LIKE 'U%'; //This finds all the countries that have the pattern starting with 'U'
SELECT country FROM food WHERE country like 'U' || '%'; // same as above.
SELECT country FROM food WHERE country like '%' || 'a'; // all ending with 'a'.
Note: || is used for concatenation in PG unlike in prog. languages.
CREATE TABLE visited_countries (
	id SERIAL PRIMARY KEY,
	country_code CHAR(2) NOT NULL UNIQUE
);
country_code CHAR(2) NOT NULL UNIQUE // NOT NULL allows us to keep it not empty, and UNIQUE allows to not to repeat the values. Otherwise, the dB will throw exception. 
``` 
###### INSERT Data
Syntax to insert data into a dB: **"INSERT INTO table_name (col1, col2, ..) VALUES (val1, val2, ..)"**
ex: *INSERT INTO food (country, rice, wheat) VALUES ('Italy', 1.46, 7.3);* // DIRECTLY IN QUERY TOOL. 
But, in Javascript, use below syntax:
*db.query("INSERT INTO food (country, rice, wheat) VALUES ($1, $2, $3)", ["Italy", 1.46, 7.3]);*
``` Sample INSERT Code:
        queryText = `INSERT INTO visited_countries(country_code) VALUES ($1)`;
        const values = [`${country_code}`];
        console.log(queryText, values);
        try {
          await db.query(queryText, values);
          console.log(result);
        } catch (e) {
          console.log("Error: ", e);
        }
```
https://node-postgres.com/features/queries