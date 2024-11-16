# Welcome To Placenet App!

## Information on our Repository
This is the default branch for Placenet, our React Native mobile application. 
   * Our **main** branch is protected as operational code, and there are no direct commits.
   * The **development** branch is a result of merging feature branching branches
   * Our features are encapulated into branches for modularity, they are labeled:
     * FB--[feature branch name]: for **front end** features

## Replicating via Docker (recommended)

Visit the [docker repository](https://github.com/angelesmarin/PlacenetDocker) for full docker instructions.

## Manual Set-up
This document will be a step by step manual on how to set up running the Placenet App on your local environment. 

Before getting started, make sure you have a code editor for running (we use Visual Studio Code)
- VS Code: https://code.visualstudio.com/download

Download the Expo Go app on your mobile device for mobile testing.
- Expo Go: https://expo.dev/go

Also make sure to have PostgresSQL installed
- PostgresSQL: https://www.postgresql.org/download/

PGAdmin is also recommended for those not well-versed in PostgresSQL
- PGAdmin: https://www.pgadmin.org/download/

Insomnia is also recommended for testing the database:
- Insomnia: https://insomnia.rest/download 

## Set-Up

1. Clone the frontend using: 

   `git clone https://github.com/angelesmarin/Placenet-App-Frontend.git`

2. Clone the backend using:

   `git clone https://github.com/angelesmarin/Placenet-App-Backend.git `

3. CD into both directories and run `npm install` to install the required dependencies for both.

4. Create a PostgreSQL database:

    - Name it "placenet"

    - Enter the following SQL to set up the proper tables and collumns:
    
      - `CREATE TABLE users (
      user_id SERIAL PRIMARY KEY,
      username VARCHAR(50) UNIQUE NOT NULL,
      password_hash VARCHAR(255) NOT NULL,
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
      );`
  
      - `CREATE TABLE properties (
      property_id SERIAL PRIMARY KEY,
      user_id INT REFERENCES users(user_id) ON DELETE CASCADE,
      name VARCHAR(255) NOT NULL,
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
      );`
  
      - `CREATE TABLE projects (
      project_id SERIAL PRIMARY KEY,
      property_id INT REFERENCES properties(property_id) ON DELETE CASCADE,
      user_id INT REFERENCES users(user_id) ON DELETE CASCADE,
      name VARCHAR(255) NOT NULL,
      description TEXT,
      start_date DATE,
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
      );`
  
      - `CREATE TABLE documents (
      document_id SERIAL PRIMARY KEY,
      project_id INT REFERENCES projects(project_id) ON DELETE CASCADE,
      user_id INT REFERENCES users(user_id) ON DELETE CASCADE,
      file_name VARCHAR(255) NOT NULL,
      file_path VARCHAR(255) NOT NULL,
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
      );`

    Or just use PGAdmin and create the tables following the specs in the above SQL.

5. In the backend directory, create a file called ".env" and put the following in it:
    - `DB_NAME=placenet`
    - `DB_USER=postgres`
    - `DB_PASSWORD=yourpasswordhere`
    - `DB_HOST=127.0.0.1`
    - `DB_PORT=5432`
    - `PORT=3000`

    **THIS FILE IS REQUIRED OR THE PROJECT WILL NOT FUNCTION**

6. Navigate to the [api.js script](https://github.com/angelesmarin/Placenet-App-Frontend/blob/development/API/api.js) and change `localhost` to your own IP.

7. Connect to the database with:

    - `psql -U postgres -d placenet`
    - Or connect to it in PGAdmin

    Enter your postgres password when prompted in either case.

8. Start the backend by running the following while cd'd into the backend directory:

    > node startServer.js backend

9. Start the frontend by running the following while cd'd into the frontend directory:

    > npx expo start

**THE DATABASE, BACKEND, AND FRONTEND MUST ALL BE OPERATIONAL**

10. Use SQL to insert a user with username and password columns specified, or use Insomnia to do so with a POST request using http://localhost:3000/api/users and some json as the body that looks like this:

    - `{"username": "usernamehere","password_hash": "passwordhere"}`

11. Upon opening the frontend, you should now be able to log in with the parameters specified in your request from step 8 and use the app.

12. To stop the processes, simply press Ctrl/Cmd + C in all the command windows, or just close the windows.

## Potential Errors

If you find that you cannot log in to the app using the user profile created in step 10, do the following:

1. Double check your spelling. The username and password is case sensitive.
2. Ensure the password column in the database is called "password_hash" and not just "password".
3. Double check that the IP in the [api.js script](https://github.com/angelesmarin/Placenet-App-Frontend/blob/development/API/api.js) is your own IP.

Insomnia can also be used to ensure the database itself is operational.

## Running App on Device
1. Open EXPO GO mobile application on your device
2. Scan QR code displayed from the terminal

### Optional: Running App on Web Browser 
   *  In code editor terminal, select W to launch the app on your local web browser.

## Testing the App
  * Log into the app using "lala" in both username and password fields and play around with the features. You should be able to add, edit, and delete properties, projects, and uploaded documents.

### For more information, visit Expo website: https://expo.dev/ 
