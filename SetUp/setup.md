# Setup
The application can easily be demoed [using this url](http://bizbazaarbizbazaarappeb-frontend-env.eba-rzd5q64x.us-east-1.elasticbeanstalk.com/)

## Manual Setup
The application can run locally by following these steps.
1. Clone both the frontend and backend repositories.
2. Install [Spring Tools Suite](https://spring.io/tools), this will run your backend.
3. Install [VSCode](https://code.visualstudio.com/), or [MingGW-w64](https://www.mingw-w64.org/), this will allow you to use a CLI interface to run the frontend application.
4. The backend will require Enviorment Variables for the application.yml to access. They can be found [here]().
5. Once Enviorment Variables are setup, you can run you backend application as a Spring Application.
6. Navigate to the base of the Frontend application.
7. Change baseURL in the eCommerceClient.ts file to *http://localhost:8080*
8. Run the cli command, **NPM --install** then **NPM start**. NPM must be installed on your machine.
9. The application will automatically run in your webbrowser.