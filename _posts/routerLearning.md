# What is the use of router?

It helps in breaking and routing different pages and simplifies the routing to different pages.

---

# How can we do it?

- Express offers us a router package, which we use to redirect to the appropriate page.
- We create a folder called `routes`.
- Inside that folder, we create route files — for example, `admin.js`.

## Inside `admin.js`

- Export Express:  
  `const express = require('express');`

- Use the router method of Express:  
  `const router = express.Router();`

- Establish respective pages using this router:  
  `router.get('/add-product', (req, res, next) => { ... })`  
  `router.post('/product', (req, res, next) => { ... })`

- Export the router:  
  `module.exports = router;`

---

## Inside `app.js`

- Import Express and body-parser:  
  `const express = require('express');`  
  `const bodyParser = require('body-parser');`

- Create the app:  
  `const app = express();`

- Import the route:  
  `const adminRoutes = require('./routes/admin');`

- Use body-parser middleware:  
  `app.use(bodyParser.urlencoded({ extended: false }));`

- Mount the router:  
  `app.use('/admin', adminRoutes);`

- Add a fallback route:  
  `app.use((req, res, next) => { res.status(404).send('<h1>Page not found</h1>'); });`

- Start the server:  
  `app.listen(3000);`
