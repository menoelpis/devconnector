** Initial Setup

> npm init
> npm i express mongoose passport passport-jwt jsonwebtoken body-parser bcryptjs validator
> npm i -D nodemon

```javascript
const express = require('express');
const app = express();
app.get('/', (req, res) => res.send('Hello World!'));
const port = process.env.PORT || 5000;
app.listen(port, () => console.log(`Server running on port ${port}`));
```

> package.json setup
```json
"scripts": {
  "start": "node server.js",
    "server": "nodemon server.js"
}
```

> npm run server -> check localhost:5000

** MongoDB Connection Key Setup

> create config folder with keys.js [config/keys.js]

```javascript
module.exports = {
  mongoURI: 'mongodb://kainos:shema1537@ds013966.mlab.com:13966/devconnector'
};
```

** DB Setup in server.js

```
// DB Config
const db = require('./config/keys').mongoURI;

// Connect to MongoDB
mongoose
  .connect(db)
  .then(() => console.log('MongoDB Connected'))
  .catch(err => console.log(err));
```

** create routes folder & routes/api folder
** create posts.js profile.js users.js files under api folder

** put posts profile users const in server.js
```
const users = require('./routes/api/users');
const profile = require('./routes/api/profile');
const posts = require('./routes/api/posts');
...
// User Routes
app.use('/api/users', users);
app.use('/api/profile', profile);
app.use('/api/posts', posts);
```


