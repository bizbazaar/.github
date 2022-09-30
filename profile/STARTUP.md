# BizBazaar Startup

Table of Contents |
----------------- |
[Local Environment](#local-environment)|
[AWS Deployment](#aws-deployment)|

## Local Environment

### Frontend
1. Clone the [repository](https://github.com/bizbazaar/bizbazaar-frontend).
2. Run `npm install` to install dependencies.
3. Navigate to `src\remote\e-commerce-api\eCommerceClient.ts` and change the following properties:
    - `baseURL` to `http://localhost:8080`
    - `Access-Control-Allow-Origin` to `http://localhost:3000`
4. Run `npm start` to start frontend.

### Backend
1. Clone the [repository](https://github.com/bizbazaar/bizbazaar-backend).
2. Create either a local or remote PostgreSQL database.
3. Create a new run configuration to run the project as a Spring Boot App.
4. Set the following environment variables in the run configuration:
    - `DB_URL` - The connection string for the database (jdbc:postgresql://HOST:PORT/DATABASE)
    - `DB_USERNAME` - The username for the database connection.
    - `DB_PASSWORD` - The password for the database connection.
5. Run using the run configuration to start backend.

## AWS Deployment

Both the frontend and backend repositories include a Dockerfile and buildspec.yml for AWS deployment.

### Overall
1. Create a new application for this project in Elastic Beanstalk.

### Frontend

1. Create a new web server environment in the Elastic Beanstalk application for the project, choosing Docker as the platform.
2. Create a new CodePipeline.
3. Select GitHub (Version 2) as the source and either create a connection to the bizbazaar GitHub organization or select the connection if it already exists.
4. Select the main branch of the bizbazaar-frontend repository.
5. Select CodeBuild as the build provider and create a new project for it.
6. Ensure that the concurrent build limit is enabled and set to 1.
7. Set an environment variable called `SONAR_TOKEN` with a SonarCloud user token.
8. Select Use a buildspec file.
9. Select the Elastic Beanstalk environment created earlier.

### Backend

1. Create a new web server environment in the Elastic Beanstalk application for the project, choosing Docker as the platform.
2. Create a new CodePipeline.
3. Select GitHub (Version 2) as the source and either create a connection to the bizbazaar GitHub organization or select the connection if it already exists.
4. Select the main branch of the bizbazaar-backend repository.
5. Select CodeBuild as the build provider and create a new project for it.
6. Ensure that the concurrent build limit is enabled and set to 1.
7. Set the following environment variables:
    - `DB_URL` - The connection string for the database (jdbc:postgresql://HOST:PORT/DATABASE)
    - `DB_USERNAME` - The username for the database connection.
    - `DB_PASSWORD` - The password for the database connection.
    - `SONAR_TOKEN` - The user token generated on SonarCloud.
8. Select Use a buildspec file.
9. Select the Elastic Beanstalk environment created earlier.
