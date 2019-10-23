This is a simple react application

```bash
# This starts a development server
npm run start

npm run test

# This builds the production ready application
npm run build

docker build -f Dockerfile.dev .
docker run -p 3000:3000 92db3b3d5914
```

After changing the src/App.js file the result is not shown in the browser.
We have to rebuild the project to get the updated version.

This is done be docker volume which is a placeholder in the docker container.

```bash
# The following run gives an error
# There is no node_modules
docker run -p 3000:3000 -v $(pwd):/app 89cb8db163e5

# The first volume says that folder is not on the computer
# but inside the container
docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app 89cb8db163e5
```

Using docker-compose file with our react application
```bash
docker-compose up --build
```

Is it important to copy the file instead only reference those?
The answer is no!
```Dockerfile
FROM node:alpine

WORKDIR /app

RUN npm install

CMD ["npm", "run", "start"]
```
How to build the production ready application?
Using a multi process dockerfile
```bash
docker build .
docker run  -p 8080:80 5d675ab07505
```


## Using github.com
```bash
git init
git add .
```
