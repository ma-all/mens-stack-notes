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
- Initialize a node project with `npm init -y`
- Install express `npm i express`

### Write Server Boilerplate
server.js <-- file name
```js
//bring express into our server
const express = require('express') 
const app = express()

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
