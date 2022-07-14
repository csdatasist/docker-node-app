### Setup: Basic Express app 

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

### Setup: Docker Image 

1. create docker file -> 'Dockerfile'

1. get image
    ```docker
    FROM node:15
    ```

1. set working directory (optional)
    ```docker
    WORKDIR /app
    ```

1. copy json file
    ```docker
    COPY package.json . # current_path docker_path 
    ```

1. install dependencies
    ```docker
    RUN npm install
    ```

1. copy code, docker caches code at each layer
    ```docker
    COPY . ./
    ```

1. expose port
    ```docker
    EXPOSE 3000
    ```

1. run 
    ```docker
    CMD ["node", "index.js"]
    ```

1. complete code
    ```docker
    FROM node:15
    WORKDIR /app
    COPY package.json . 
    RUN npm install
    COPY . ./
    EXPOSE 3000
    CMD ["node", "index.js"]
    ```

1. add ignore files -> .dockerignore
    ```
    node_modules
    Dockerfile
    .dockerignore
    .git
    .gitignore
    steps.md
    ```

1. build image and run container
    ```
    docker build -t node-app-image . 
    docker run -p 3000:3000 -d --name node-app node-app-image
    ```
Docker Commands:
```bash
# list docker images
docker image ls 

# delete image
docker image rm 423dsqrw

# list running containers
docker ps 

# delete container
docker rm node-app -f 

# enter docker container, exit to leave
docker exec -it node-app bash
```
