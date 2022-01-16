### QA Automaton Framework Setup
# Cypress

This document is created to enable new employees to get the basic, starting knowledge on how web automation testing works.

**Main task:**

Ensure the quality of the products that your team puts in in the hands of customers by automatig web application end users processes.

**Pre-Requisites:**

+ Install [git](https://git-scm.com/) (Version Control System)
+ Make sure you have access to git repo: (https://git.nosolutions.rs/)
+ Make sure you have ssh access to your account and key is already added for account.
+ Install [VSCode](https://code.visualstudio.com/) (Integrated Development Environment)

## 01. Installation Steps

+ Install [JDK 11](https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html) for Windows
    + Setup environment variables for Java within your PS:
        + Do: WIN + env + ENTER
        + Click on: "Environment Variables" button in the bottom right corner on window
            + JAVA_HOME (C:\Program Files\Java\jdk-11.0.12)

**Create a new project**

- Create working folder:
	- C:\Users\user\Documents\TestProjects\CypressProject
- Type and follow instructions:
	-  npm init
- Install Cypress: npm install cypress --save-dev (Latest version)
	- npm install cypress@6.8.0 --save-dev
	- npm install cypress@6.9.1 --save-dev
	- npm install cypress@7.7.0 --save-dev
- Start Cypress Test Runner (type in CMD or VSCode terminal): 
 	- node_modules\.bin\cypress open (Run in background)
	- node_modules\.bin\cypress open —headed (Run in UI)

**Clone project**

- Create working folder:
	- C:\Users\user\Documents\TestProjects\CypressProject
- Clone application under test
	- Type the following commands:
		- git clone https://github.com/filiphric/cypress-tau-course.git
		- npm install (install all dependencies)
		- npm start (in browser type: http://localhost:4200/)
- Clone application outside test
	- Type the following commands:
		- git clone https://git.nosolutions.rs/vladan.furman/dating.git
		- npm install (install all dependencies)
		- npm start (in browser: http://localhost:4200/)

## 02. Brief details about the files and folders

- project_name/dating (root)
	- cypress
		- **fixtures** (This folder contains CSV, HTML, or JSON files)
			- example.json
			- example.csv
		- **integrations** (This folder provides a place that writes out test cases)
			- 01_SD_Smoke_Tests
				- 01_01_test_landing_page_eng.spec.js
				- 01_02_test_landing_page_ger.spec.js
			- 02_SD_Regression_Tests
				- 01_landing_page
					- 01_01_test_landing_page_eng.spec.js
					- 01_02_test_landing_page_ger.spec.js
				- 02_signup
					- 02_01_test_signup_form_eng.spec.js
					- 02_02_test_signup_form_ger.spec.js
				- 03_registration
					- 03_01_test_signup_form_eng.spec.js
					- 03_02_test_signup_form_ger.spec.js
				- 04_login
					- 04_01_test_login_eng.spec.js
					- 04_02_test_login_ger.spec.js
		- **plugins** (This folder contains the plugins or listeners)
			- index.js
		- **reports** (This folder contains html reports runnable within your browser)
			- mocha
			- mochareports
		- **support** (Writes customized commands or reusable methods that are available for usage in all of your spec/test files.)
			- page_objects
				- helpers.js (Functions or actions. E.g. delete all photos, select language, api - post actions, api - setup default state)
				- navigations.js (Functions or actions. E.g. navigate to log in, navigate to profile menu, navigate to search tab)
				- login.js (Functions or actions. E.g. login different users)
			- commands.js (This file contains commands for starting different environment and to store .json file from fixture folder before test start)
                - Cypress.Commands.add('openApplication')
                - cy.visit('Cypress.env(url)')
                - cy.fixture('users')
			- index.js (This file is processed and loaded automatically before your test files. Global configuration. Behavior that modifies Cypress)
                - import './commands' (This is by default)
		- **videos** (This folder contains videos that will be saved after test execution)
			- 01_SD_Smoke_Tests
			- 02_SD_Regression_Tests
    	- **node_modules** (This is the folder where NPM installs all the project dependencies.)
 	- **cypress.env.json** (This file contains different development stages)
		- “devUrl”: https://develop.xxxxx.date
		- “stageUrl”: https://staging.xxxxx.date
	- **cypress.json** (This file contains different Cypress configurations options. E.g., timeout, base URL, test files, or any other configuration.)
        - "chromeWebSecurity": false
        - "defaultCommandTimeout": 15000
        - "requestTimeout": 15000
        - "screenshotsFolder": "cypress/reports/mochareports/assets"
        - ...
	- **e2e-run-tests.js** (This file contains run commands)
        - cypress.run (spec: "test.spec.js")
	- **package.json** (This file contains scripts, and dependencies used in our scripts)
		- scripts: (We use these commands to run scripts from the terminal or commander)
		    - “cypress:open”: “node_modules\\.bin\\cypress open”
			- “cypress:run”: “cypress run —headless —browser chrome”
		- devDependencies:
			- cypress: 6.9.1
			- cypress-file-upload: 5.0.6
			- cypress-iframe: 1.0.1
			- cypress-multi-reporters: 1.5.0
			- cypress-wait-until: 1.7.1
			- cy-mobile-commands: 0.2.1
			- mocha: 8.3.2
			- mochawesome: 6.2.2
			- mochawesome-merge: 4.2.0
			- mochawesome-report-generator: 5.2.0
			- moment: 2.29.1
	- **package-lock.json**

#### Additional Details:

- **Fixtures** 
are external pieces of static data that can be used by your tests. We should not hard code data in the test case. It should drive from an external source like CSV, HTML, or JSON. They will be majorly used with the cy.fixture() command when you need to stub the network calls. 
- **Integration**
folder provides a place that writes out test cases. It also provides an “examples” directory, which contains the default test cases provided by Cypress and can be used to add new test cases also. We can also create our folder under the integration directory and add out test cases under that.
- **Plugins**
contain the plugins or listeners. By default, Cypress will automatically include the plugins file “cypress/plugins/index.js” before every test it runs. You can programmatically alter the resolved configuration and environment variables using plugins, Eg. If we have to inject customized options to browsers like accepting the certificate, or do any activity on test case pass or fail or to handle any other events like handling screenshots. They enable you to extend or modify the existing behavior of Cypress. 
- **Support**
writes customized commands or reusable methods that are available for usage in all of your spec/test files. This file runs before every single spec file. That’s why you don’t have to import this file in every single one of your spec files.  The “support” file is a great place to put reusable behavior such as Custom Commands or global overrides that you want to be applied and available to all of your spec files. 
- **Node_Modules**
in the default project structure is the heart of the cypress project. All the node packages will be installed in the node_modules directory and will be available in all the test files. So, in a nutshell, this is the folder where NPM installs all the project dependencies. 
- **Cypress.json** 
is used to store different configurations. E.g., timeout, base URL, test files, or any other configuration that we want to override for tweaking the behavior of Cypress. We can also manage the customized folder structure because it is part of by default Cypress Configurations.

## 03. Basic Cypress Actions

- Navigate to the web page you want to test (cy.visit)
- Locate the element of the web page you want to test and perform action (cy.get('button').click())
- Run script from Cypress runner
- Run script with command from terminal and generate report and logs (node_modules\.bin\cypress run --spec "cypress\integration\examples\firsttest.js")
- Navigate to report\mochareports\report.html

## 04. Tips
- Organize your tests - separate and categorize them
	- Create folders to more accurately categorize files
	- Split tests by category, e.g. in the 'user' folder put tests for login and registration, and in the 'shopping' folder - tests for the buying process.
- Write independent tests
	- You should be able to choose any test or run several tests in any order and still get the same result.
- Set base URL
	- Instead of repeating the lines with web addresses in each test, set the base URL in the 'cypress.json' file.
- Run tests, that are crucial at the moment - use ‘cy.only’ and ‘cy.skip’
- Use your own custom commands
	- Add your command to the 'commands.js' file
- Use the best selectors (CSS, By ID, By ClassName)
- Add assertions - to be sure that you are referring to the right element at the right time instead of wait(500).
	- should('contain.text', 'Login') 
	- should('be.visible')

## 05. Tutorials and Useful Links
- https://docs.cypress.io/
- https://www.udemy.com/course/cypress-web-automation-testing-from-zero-to-hero/
- https://www.youtube.com/watch?v=gUFdU5fQs4o&list=PLSRQwlkmpdj6K7pwZmu9v5icbhAiGlQln&ab_channel=Cypress.io
- https://www.youtube.com/watch?v=avb-VDa3ZG4&t=2637s&ab_channel=LaithHarb
- https://www.youtube.com/watch?v=CYcdT-tOvB0&list=PLhW3qG5bs-L9LTfxZ5LEBiM1WFfvX3dJo&ab_channel=AutomationStepbyStep
- https://www.diogonunes.com/blog/cypress-tips-tricks/
