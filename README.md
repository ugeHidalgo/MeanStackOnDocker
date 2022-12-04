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
    npm-debug.log

2- Add DockerFile on client folder with the following content:
    FROM node:carbon #Base image on Node carbon, giving access to npm and node.
    WORKDIR /usr/src/app #working directory inside the container, making it possible to reference this directory with “.”

    # Install app dependencies
    # A wildcard is used to ensure both package.json AND package-lock.json are copied
    # where available (npm@5+)
    COPY package*.json . #Copying package.json and package-lock.json to the working directory inside the image

    # Install any needed packages
    RUN npm i # Runs npm install at the working directory

    # Bundle app source
    COPY . . #Copy all from current directory (if not in .dockerignore file) to working directory

    EXPOSE 4200 #Showing that the app is to be exposed on port 4200 (but only actually exposed on port 4200 if we specify this in the “docker run” command using the -p parameter).
    CMD [ "npm", "start" ] #Specifying that the default command should be npm start. This can be overridden, if wanted, by specifying another command in “docker run”.

3- Launch docker desktop and wait for engine to be started.
4- Move to client folder
5- Run command 'docker build -t meanstackapp:1.0 .'

## Docker run:
docker run -p 4200:4200 meanstackapp:1.0