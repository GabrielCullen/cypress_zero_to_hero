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
* No testing on mobile or mobile devices - can only use web mobile view
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

To setup the configuration of the project we go to `cypress.config.js` and we can use guidance from the [cypress docs](https://docs.cypress.io/guides/references/configuration#e2e). For the purposes of this tutorial, we are setting the viewport to be the resolution of the screen. This is set to be global so will apply outwith just the end to end testing. We changed the port number to match the local port that we are hosting the project on. Next, the `specPattern` is altered to negate the need for `.cy.js` extension - we can just use `.js`. This does not seem to be the *modern* way of doing things and may be an unnecessary step in practice. Lastly we add an `excludeSpecPattern` to hide the demo files that were created earlier. The finished `cypress.config.js` can be seen below.

```js
const { defineConfig } = require('cypress')

module.exports = defineConfig({
  viewportHeight: 1080,
  viewportWidth: 1920,
  e2e: {
    baseUrl: 'http://localhost:4200',
    specPattern: "cypress/e2e/**/*.{js,jsx,ts,tsx}",
    excludeSpecPattern: ["**/1-getting-started", "**/2-advanced-examples/*"],
    
  }
})
```

A new file was created in the `e2e` folder - `firstTest.spec.js` - if configured correctly this should now show up in the cypress runner. Indeed when starting cypress again, this file was discovered and added as a test however, as it has no content, it simply throws an error when ran.

*Note: cypress has to be run from the project root folder, otherwise you will be creating a new instance of cypress at a different location.*