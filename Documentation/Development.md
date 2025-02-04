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
  

## Set-Up

1. Clone the frontend using: 

   `git clone https://github.com/angelesmarin/Placenet-App-Frontend.git`

2. Run `npm install` to install the required dependencies.
   - Be sure to repeat this command when pulling updated builds from the repo to ensure you have all of the up-to-date dependencies.

3. Obtain the necessary firebaseConfig.js file, create a folder called `config` in the Placenet-App-Frontend folder, and place the firebaseConfig there. The app will not connect to the Firebase backend without it.
    
4. Start the project by running the following while cd'd into the directory:

    > npx expo start

5. To stop the process, simply press Ctrl/Cmd + C in the command window, or just close the window.
   
   

## Potential Errors

If you find that you cannot log in to the app using the user profile you signed up for, double check your spelling. The username and password is case sensitive.



## Running App on Device
1. Open EXPO GO mobile application on your device
2. Scan QR code displayed from the terminal

## Testing the App
  * Either sign in with your account or sign up for one in the app with your email.
  * Run `npx jest` to run the test cases, and `npx jest --coverage` for a coverage report.

### For more information, visit Expo website: https://expo.dev/ 
