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
