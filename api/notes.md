Follow the instructions given here
https://github.com/CloudNativeJS/docker

### Building the Docker image for Mern api server

Run the following command from inside the api directory where Dockerfile is available, :

```
docker build -t mernapiserver -f Dockerfile .
```

here `.` means current directory

### Running the Docker image for MERN API Server

After the Docker image has been created for Mern api server, you can run it using either of the following commands:

- Run as an interactive application on your command line:

  ```
  docker run -i -p 8080:8080 -t mernapiserver
  ```

  This maps port 8080 in the Docker image to port 8080 on your machine. If you are using a different port, you will need to change the mapping.

- Run as a daemon process:
  ```
  docker run -d -p 8080:8080 -t mernapiservers
  ```
  This uses the `-d` flag rather than the `-i` flag to run the Docker image as a background task.

### Creating Docker image for development

Run the following command from inside the directory where Dockerfile is available, :

```
docker build -t mernapiserver-tools -f Dockerfile-tools .
```

here `.` means current directory

### Running the Docker tools image for MERN API Server: Development Mode

Running the image in Development Mode uses `nodemon` to watch for changes in the application and automatically restart it as those changes are made.

To enable the local changes to be updated in the Docker image, you must map your local file system into the running Docker container, as follows:

1. Generate a Linux version of your `node_modules` dependencies locally, by generating them inside the node:10 docker image:

```sh
docker run -i -v "$PWD"/package.json:/tmp/package.json -v "$PWD"/node_modules_linux:/tmp/node_modules -w /tmp -t node:10 npm install
```

This step only needs to be repeated if you modify your package.json file.

2. Run the Docker tools image as an interactive application on your command line in dev mode:

```sh
docker run -i -p 8080:8080 -v "$PWD"/:/app -v "$PWD"/node_modules_linux:/app/node_modules -t mernapiserver-tools /bin/run-dev
```

This maps port 8080 in the Docker image to port 8080 on your machine. If you are using a different port, you will need to change the mapping.
This command also maps your local directory into the Docker container, allowing you to modify your Node.js application code and see the changes running immediately in the container.
