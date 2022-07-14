### Set Up: Basic Express app 

1. create node app
    ```
    npm init 
    ```
1. install express
    ```
    npm install express
    ```
1. create app.js file
    ```js
    const express = require('express');

    const app = express();

    const port = process.env.PORT || 3000

    app.get('/', (req, res) => {
        res.send('hello world');
    })

    app.listen(port, () => console.log(`app is listening on ${port}`) );
    ```
1. run 
    ```
    node app.js 
    ```