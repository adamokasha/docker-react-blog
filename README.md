# React Redux Blog w/ API - Dockerized Version

## About

React Redux Blog and API are two repos joined into one in this repository using docker. The db is mongo using a docker image.

### [Link to React-Redux Blog](https://github.com/adamokasha/react-redux-blog)

### [Link to Blog API](https://github.com/adamokasha/node-blog-api)

## Running Locally (Docker required)

### Environment variables

1. Create an `.env.local` file in the `react-redux-blog` directory.
2. Add the following line:
   REACT_APP_API_URL=http://localhost:4000
3. In the `node-blog-api/server/config` create a `config.json` file
4. Add the following:

```
{
  "development": {
    "MONGODB_URI": "mongodb://localhost:27017/react-redux-blog",
    "JWT_SECRET": "3qd82380wdf",
    "PORT": 4000
  },
  "dockerdev": {
    "MONGODB_URI": "mongodb://mongodb:27017/react-redux-blog",
    "JWT_SECRET": "3qd82380wdf",
    "PORT": 4000
  }
}
```

### Running the Docker Containers

This project comes with a 'hot-reload' docker environment via:

- Mounting the files the CRA dev server is watching as volume
- Similarly mounting volume for server application with nodemon

1. Create a volume by typing `docker volume create mongodbdata` in the terminal.
2. From root folder type `docker-compose up` or `docker-compose up --build` to force rebuild in the terminal.
3. If you would like to add post, ssh into the mongo container using the `docker exec -it <container id> /bin/bash` and modify your user in the users collection to have role as `admin`.
