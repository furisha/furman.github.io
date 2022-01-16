### QA Automation Framework Setup 
# Java + Selenium + Cucumber + TestProjectIO

This document is created to enable new employees to get the basic, starting knowledge on how web automation testing works.

**Main task:**

Ensure the quality of the products that your team puts in in the hands of customers by automatig web application end users processes.

**Pre-Requisites:**

- Make sure you have access to [company git repository](https://git.nosolutions.rs/)
- Make sure you have ssh access to your account and key is already added for account.
- Must have account on Test Project cloud platform: [TestProjectIO](https://testproject.io/)
- Run: TestProject Agent on your PC (If using [TestProjectIO SDK](https://docs.testproject.io/testproject-sdk/opensdk-v2/java-sdk) instead of chromedriver)
- Install [IntelliJ IDEACommunity Edition](https://www.jetbrains.com/idea/download/#section=windows)

## 01. Installation steps

- Install [JDK 11](https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html) for Windows
    - Setup environment variables for Java within your PS:
        - Do: WIN + env + ENTER
        - Click on: "Environment Variables" button in the bottom right corner on window
            - JAVA_HOME (C:\Program Files\Java\jdk-11.0.12)
- Download [Maven (zip)](https://maven.apache.org/download.cgi)
- Create folder (C:\Program Files\apache-maven-3.6.3), copy and unzip maven file.
- Setup environment variables for Maven:
    - System Properties\Advanced\Environment Variables:
        - MAVEN_HOME (C:\Program Files\apache-maven-3.6.3)
- Install [NodeJS 14.17.6](https://nodejs.org/en/blog/release/v14.17.6/)
- System Properties\Advanced\Environment Variables\Path:
    - Within the Path set environment variable: 
        - %JAVA_HOME%\bin
        - %MAVEN_HOME%\binF
- Download [Chromedriver](https://chromedriver.chromium.org/downloads)
- Download [Selenium](https://www.selenium.dev/downloads/)
- Within your terminal navigate to: C:/Users/Username/Documents/TestingProjects/Selenium/
- Clone project repository: git clone https://git.nosolutions.rs/vladan.furman/onboarding-selenium.git
- Open project with IntelliJ Idea
- Run first test with Maven
- Optional:
    - Download and install [TestProjectIO](https://testproject.io/)
    - Run TestProjectIO Agent
    - Setup [TestProjectIO Java SDK](https://www.youtube.com/watch?v=PuwS0FiF9to&list=PLGLlPuoTA3DURLLEpkJJmN7wXgGztfIo3&index=5&t=1068s&ab_channel=UltimateQA)

## 02. Brief details about the files and folders

- project_name/sauce-demo
    - Resources (This folder contains drivers etc chromedriver, geckodriver...)
    - src/main/java/com.bwl/ (package folder)
        - BaseClass.java (setDriver, driverQuit)
        - LoginPage.java (waitForLogoPresence, clickOnLoginButton)
    - test/java/com.bwl/ (package folder)
        - StepDefinitions/ (package folder)
            - Initialize.java (Before - setDriver, After - driverQuit)
            - LoginStepDefinitions.java (Given, Then, When...)
    - TestRunner (RunWith - CucumberOptions)
    - test/resources
        - features
            - LoginUser.feature (Cucumber Features and Scenarios: Given, Then, When, Examples )
        - cucumber.properties
    - target
        - classes
        - cucumber-reports
        - generated-sources
        - generated-test-sources
        - test-classes
    - pom.xml (This file contains all dependencies and plugins)

## 03. Dependencies list (pom.xml)

- build
	- plugins
		- plugin:
----
			- groupId: org.apache.maven.plugins
			- artifactId: maven-surefire-plugin
			- version: 3.0.0-M5
				- configuration:
					- suiteXmlFile: testng.xml
----
			- groupId: net.masterhought
			- artifactId: maven-cucumber-reporting
			- version: 5.3.0
----
- dependencies
	- dependency:
----
		- groupId: io.testproject
		- artifactId: java-sdk
		- version: 1.2.3.-RELEASE
----
		- groupId: org.seleniumhq.selenium
		- artifactId: selenium-java
		- version: 3.141.59
----
		- groupId: org.testng
		- artifactId: testng
		- version: 7.3.0
----
		- groupId: io.cucumber
		- artifactId: cucumber-java
		- version: 6.7.0
----
		- groupId: io.cucumber
		- artifactId: cucumber-testng
		- version: 6.7.0
----
		- groupId: io.cucumber
		- artifactId: cucumber-core
		- version: 6.7.0
----
		- groupId: org.junit.jupiter
		- artifactId: junit-jupiter-api
		- version: 5.5.2
----
		- groupId: io.cucumber
		- artifactId: cucumber-junit
		- version: 6.11.0
----

- properties
    
----
	- maven.compiler.source: 11
	- maven.compiler.target: 11
----

## 04. Basic selenium actions

- Instantiate a WebDriver object to drive the browser you want to use in your test
- Navigate to the web page you want to test
- Locate the element of the web page you want to test
- Ensure that the browser is in the correct state to interact with that element
- Perform the action on the element
- Record test results
- Create report and logs
- Quit the test

## 05. Tips

- Html DOM consists of: HTML Tags, HTML Attributes and Attributes values
- Class and ID are also HTML attribute names
- Class attribute can have several values and each value is separated by space
- HTML tags usually come in pairs of Opening and Closing tag. Closing tag has the same name and forward slash
- Value in between angle brackets (>here<) is a plain text
- Elements above the “key” web element are Parent elemens
- Elements inside of the “key” Element are Child Elements
- Elements placed at the same level side by side are Sibiling Elements
- Remember to use the best locators (never use absolute XPath or absolute CSS).
- ID and data attributes are the best for locating elements.

## 06. Tutorials and useful links

- https://www.selenium.dev/documentation/webdriver/
- https://github.com/nadvolod/selenium-java
- https://www.youtube.com/watch?v=aIfP8rOx66E&t=1825s&ab_channel=UltimateQA
- https://www.youtube.com/watch?v=Xjv1sY630Uc&t=189s&ab_channel=TechWithTim
