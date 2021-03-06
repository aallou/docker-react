# Specific doc
## Generate project steps
npm install -g create-react-app<br>
create-react-app react-example

## Build docker image for dev env
docker build -f Dockerfile.dev .

## Run a container (with automatic reload if react files changed)
docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image_id>
or
docker-compose up --build

## Run tests in another terminal
docker exec -ti <web-container-id> npm run test

## Run prod env
For production environment, we will use Dockerfile (not Dockerfile.dev) to run our application.<br>
This image use multi-steps to build the image.<br>
At the end, we use nginx as a server for production. So, the Dockerfile build the sources (with npm run build), then we copy this "build" folder into our image.
Ngix use the 80 port (default).<br>
Build : docker build .
Run : docker run -p 8080:80 <image-id>

## Travis-ci and AWS Elastic Beanstalk
To deploy the application automatically, we use Travis-ci who build the image (dev), test it and deploy the image (based on Dockerfile) to AWS (Elastic Beanstalk).<br>

*Steps:*
- Create an environment + application on AWS (Elastic Beanstalk)
- create a user on service IAM on AWS (to get access key ans secret to be used by Travis CI to deploy)
- Add deploy script on ".travis.yml"
- Add env variables for Access key and secret key 

# Generated doc

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br>
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br>
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br>
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br>
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br>
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
