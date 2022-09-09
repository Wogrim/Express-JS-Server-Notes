## getting started

1. make a project folder, open in VS Code
2. create a **server.js** file
3. in the terminal run `npm init -y` for default npm **package.json**
4. in the terminal run `npm install express` which will download express and its dependencies (**node_modules** folder)
5. if using git, make a **.gitignore** and add *node_modules*
6. basic *server.js* code
```
const express = require('express');
const app = express();
const PORT=8000;

app.get("/api/text", (req, res) => {
    res.send("hello world"); 
});

app.get("/api/json", (req, res) => {
    res.json({
        hello: 'hello',
        world: 'world'
    });
});

app.listen(PORT, () => console.log(`Server is listening on PORT ${PORT}`));
```
7. in the terminal run `npm install -g nodemon` to have access to **nodemon** command
   - one-time install which will auto-restart the server when you modify files
8. run the server with `nodemon server.js`

## variables in the route path

route to get a specific person from the *people* array
- **id** is a key in the **req.params** object (the colon is not part of the route)
```
app.get("/api/people/:id", (req, res) => {
    res.json(people[req.params.id]);
});
```

## POST routes

before all routes we need code that will allow us to see the body of an incoming request
```
app.use(express.json());
app.use(express.urlencoded({extended:true}));
```

for the actual route to create a person
```
app.post("/api/people", (req, res) => {
    people.push(req.body);
    res.json({status:"success"});
});
```

## PUT routes

route to update a person
```
app.put("/api/people/:id", (req, res) => {
    people[req.params.id] = req.body;
    res.json({status:"success"});
});
```

## DELETE routes

```
app.delete("/api/people/:id", (req, res) => {
    users.splice(req.params.id, 1);
    res.json({status:"success"});
});
```
