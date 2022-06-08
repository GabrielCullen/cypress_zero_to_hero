# Cypress: Web Automation Testing from Zero to Hero

### Introduction

Cypress pros:

* Complete framework
* Very fast - runs in browser
* Stable
* No complex programming
* Can test and mock APIs
* A test environment is not necessary

Cypress Cons:

* No support for IE or Safari
* Asynchronous code
* No testing on mobile or mobile devices - can only usse web mobile view
* Can only test on a single domain or a single tab
* Not friendly with iFrames

### Setting up development environment

Install:

* Chrome
* Node.js
* Git
* Install IDE

(These were all in the apt repository. Probably worth also installing npm and nvm)

Run `npm install` in the project folder to retrieve dependancies
`npm start` will now launch the website at `http://localhost:4200/`

Next install cypress with `nvm install cypress --save-dev`

If necessary we can covert the created typescript files to JavaScript. I have done so in this example project. `/cypress.config.js` `/cypress/support/commands.js` `/cypress/support/e2e.js` can all be changed.

Cypress can be launched with `npx cypress open` and we can create a new instance by selecting end to end testing. We can then choose a browser, electron and chrome seem to be the best options.

If everything is configured correctly there will be an option to choose between "Scaffold example specs" and "Create new empty spec". For this project the example specs will be chosen. When this is selected cypress will automatically create an e2e folder and include some examples of tests showcasing how they should be written. These newly created sample tests can be run by clicking them in the cypress browser

Cypress will generate a "cypress" folder when it is first used. It will generate 3 sub-folders, "e2e", "fixtures" and "support". `e2e.js` is the first file that is executed after cypress is initialised. It can be used to import commands and packages. `commands.js` is the place to store custom commands. These can be commands that will be shared across the framework and we could store common events such as logging in. The `fixtures` folder is the place to store `.json` files, used for mocking API's. The `e2e` folder is where we will be storing tests. Finally, the `cypress.config.js` file is where we configure the behaviour of the framework.