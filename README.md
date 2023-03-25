## Continuous Integration and Deployment Of a Simple React Application

### Introduction

This project showcases implementation of a continuous integration and deployment (CI/CD) process.

### Final Output

The final output of the project is a working web application deployed to AWS Elastic Beanstalk. Users can access the app by visiting the Elastic Beanstalk URL. 
The CI/CD process ensures that any changes made to the code are automatically built, tested, and deployed, making it easy to make updates and improvements to the app.

### Project Structure - the CI/CD process:

![image](https://user-images.githubusercontent.com/117165801/227231485-785f781f-481b-47cb-b2cf-0d4177969da6.png)

Steps:

1. Whenever a developer issues a new Pull request in github, Travis CI will run tests over the codebase and report back if all the checks have passed.
2. As soon as a developer merges the new changes of the application to the main branch, Travis CI will automatically run tests(again), then build the Docker image for the React app and finally deploy the app in containers over to AWS Elastic Beanstalk.

   The **'Dockerfile'** and **'docker-compose.yml'** files contain the necessary configuration for building and running the Docker containers.
   The **'.travis.yml'** file defines the build and deploy stages for Travis CI.

### React App

The React app is a simple web application that displays a list of items. In this project, the app is used to demonstrates how React applications integrates with the CI/CD process using Docker, Docker Compose, Travis CI and AWS Elastic Beanstalk.

### Conclusion

This project allows rapid and reliable deployment of changes to the application.
By automating the build, test, and deployment stages, developers can deploy changes to their application with confidence and efficiency.
