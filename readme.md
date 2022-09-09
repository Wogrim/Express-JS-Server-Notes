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
