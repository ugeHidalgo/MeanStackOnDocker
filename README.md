# Client

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 15.0.2.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

## Docker build: (This will add a docker image 'meanstackapp' into the docker desktop)
1- Add .dockerignore file on client folder with the following content:
    node_modules

2- Add DockerFile on client folder with the following content:
    # Create image based on the official Node 18 image from dockerhub
    FROM node:18

    # Create a directory where our app will be placed
    RUN mkdir -p /usr/src/app

    # Change directory so that our commands run inside this new directory
    WORKDIR /usr/src/app

    # Copy dependency definitions
    COPY package.json /usr/src/app

    # Install dependecies
    RUN npm install

    # Get all the code needed to run the app
    COPY . /usr/src/app

    # Expose the port the app runs in
    EXPOSE 4200

    # Serve the app
    CMD ["npm", "start"]

3- Launch docker desktop and wait for engine to be started.
4- Move to client folder
5- Run command 'docker build -t angular-client:dev .'

## Docker run:
docker run -d --name angular-client -p 4200:4200 angular-client:dev