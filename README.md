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
