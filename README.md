## NodeJS + Passport Login

### Setting for Development

- `npm init`
- `npm i`
  - `express`: application server
  - `ejs`: templating language for views
- `npm i --save-dev`
  - devDependencies
  - `nodemon`: auto restart server
  - `dotenv`: store ENVIRONMENT variables into .env file
- create `.env` and `.gitignore`

- modify package.json

  - ```json
    "scripts": {
        "devStart": "nodemon server.js"
    }
    ```

- create server.js

<br/>

### Create Basic Server

- start the server at port 3000

  - `app.listen(3000)`

- "Cannot GET" shows up because no Routes set up

  - ```javascript
    app.get("/", (req, res) => {
      res.render("index.ejs");
    });
    ```

- create index.ejs

- > Have to tell server that we are using ejs to use ejs syntax

  - ```javascript
    app.set("view-engine", "ejs");
    ```

<br/>

### Login and Register

- create views

- create routes in server.js

- register.ejs

  - create `<form>` that contains inputs

  - `method="POST"` to `action="/register"`

    - create route for post in server.js

  - ```html
    <label for="name">Name</label>
    ```

    - this label is for **name** variable

  - ```html
    <input type="text" id="name" name="name" />
    ```

    - name="name" : how acts in server

  - `<button>` for submitting

  - `<a>` for directing to /login

- login.ejs
  - similar to register.ejs

<br/>

### Implement POST Methods - Register

- since getting information from **forms**

  - ```javascript
    app.use(express.urlencoded({ extended: false }));
    ```

    - able to access `email` and `password` inside `req` variable
    - `req.body.name`
    - `req.body.email`
    - `req.body.password`
    - corresponds to the **name field** in html

- ```javascript
  const users = [];
  ```

  - save user information in a local variable

- hash passwords

  - `npm i bcrypt`

  - ```javascript
    const hashedPassword = await bcrypt.hash(req.body.password, 10);
    ```

  - 10 : how many times to generate the hash = how secure we want the password to be

- since post accesses DB or local variable = async operation

  1. make the function async
  2. try~catch

- redirect the user to a URL when finished

<br/>

### Passport + POST - Login

- passport has many ways of logging in

  - `npm i passport passport-local`

- store and persist user across different pages => session

  - `npm i express-session`

- display messages if failed login

  - `npm i express-flash`
  - used by passport inside internals

- create `passport-config.js`

  - password defaults to "password"

  - callback function to authenticate the user

    - ```javascript
      passport.serializeUser((user, done) => {});
      ```

      - store inside the session

    - ```javascript
      passport.deserializeUser((id, done) => {});
      ```

      - since user has been serialized to a single ID, takes in id as variable

  - authenticating user function

    - ```javascript
      const authenticateUser = (email, password, done) => {};
      ```

  - getUserByEmail is passed as a function from the caller of initialize
