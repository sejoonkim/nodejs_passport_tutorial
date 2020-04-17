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
