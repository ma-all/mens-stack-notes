# Men Stack Notes (unit 2)
| CRUD Action | RESTful Action | HTTP Method | Definition |
| ----------- | -------------- | ----------- | ------------------------ |
|  | `new` | `GET` | Show a form to create a new item |
| Create | `create` | `POST` | Add a new item to the database |
| Read | `index` | `GET` | Show all items |
| Read | `show` | `GET` | Show one specific item |
|  | `edit` | `GET` | Show a form to edit an existing item |
| Update | `update` | `PUT` | Save changes to an existing item |
| Delete | `delete` | `DELETE` | Remove an item from the database |

## Setup
- Create a directory
- Create a server file `touch server.js`
- Create a `.gitignore` file
- Initialize a node project with `npm init -y`
- Install express and morgan `npm i express morgan`

### Add `node_modules` to `.gitignore`
.gitignore
```bash
node_modules
```

### Write Server Boilerplate
server.js <-- file name
```js
//bring express into our server
const express = require('express')
const morgan = require('morgan')

const app = express()

app.use(morgan('dev'))

//this should always be at the bottom, takes two arguments: port, call back function
app.listen(3000,function() {
    console.log('Listening on port 3000')
})
```
<img width="455" height="155" alt="image" src="https://github.com/user-attachments/assets/ef5f3877-6095-437a-8471-eb94b9ce3b51" />

Run the server with `nodemon server.js`

Navigate to `http://localhost:3000` to view our server.

Use `ctrl + c` to stop the server in the terminal.

### Creating a test route
```js
//test route at endpoint / test repsonds with text
app.get('/test', function(req, res){
    res.send('this is a test')
})
```
<img width="387" height="102" alt="image" src="https://github.com/user-attachments/assets/5a9c2ab7-094c-480b-93e6-19da8df9ef33" />

Navigate to `http://localhost:3000/test`

### Using request parameters
```js
app.get('/:userId', function(req, res){
    res.send(`hello ${req.params.userId}`)
    console.log(req.params.userId)
}) 
```
<img width="358" height="92" alt="image" src="https://github.com/user-attachments/assets/d5cb4f5f-7efc-4f0c-8649-3c4ac6d68445" />

Navigate to `http://localhost:3000/310` 

### Rendering EJS
- Install ejs with `npm i ejs`
- Create a `views` directory
- Create an `.ejs` file like `home.ejs`
- Add html boilerplate with `!`

home.ejs
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
</head>
<body>
    <h1>We are rendering an EJS page!</h1>
</body>
</html>
```

- Render `ejs` page using a controller like this one:
```js
app.get('/', function(req, res) {
  res.render('home.ejs') 
})
```
<img width="605" height="145" alt="image" src="https://github.com/user-attachments/assets/32e1c426-e3e3-4254-92c9-7cbd93b247e6" />

### EJS Syntax
To use javascript in an ejs file, I need a scriptlet tag:
```ejs
<% let user = 'marwa' %>
```

To display javascript values from an ejs file, I need an output tag:
```ejs
<%= user %>
```

### Pass data from the controller

Use the locals object inside the render method:
```js
res.render('home.ejs', {
    title: 'Home Page',
})
```
Now I can use the `title` variable in my `home.ejs` file.

home.ejs
```ejs
<h1><%= title %></h1>
```

### Using `forEach` in `ejs`
```ejs
<ul>
    <% inventory.forEach(function(item){ %>
      <li> <%= item.name %></li>
    <% }) %>
</ul>
```
