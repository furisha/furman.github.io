### QA Automation Framework Setup
# Python + Selenium + HTML Report

**Pre-Requisites:**

- Make sure you have access to git repo: (https://git.nosolutions.rs/)
- Make sure you have ssh access to your account and key is already added for account.
- Install PyCharm

## 01. Installation steps

- Please do the following steps to set up the framework:
    - Clone the repo & create the virtual env
    - Clone the automations repo: git clone "file"
----
- Create a virtual env:
    - python -m virtualenv venvs\automations
----
- Activate the virtualenv:
    - . .\venvs\automations\bin\activate
----
- Install dependencies (this can be done from pycharm):
    - selenium==3.14.1
	- requests==2.23.0
	- pytest==6.0.1
	- pytest-html==2.0.1
	- pytest-xdist==2.5.0
	- openpyxl==3.0.9
	- pytest-metadata==1.10.0
	- PyYAML==5.3.1
	- c- lang==4.0.post1
	- urllib3==1.25.10
	- allure-pytest==2.8.40
	- stripe==2.37.2
	- pytz==2020.1
	- pytest-services==2.2.1
----
- Install Chromedriver
    - Make sure your version of Chrome is up to date, and install the latest Chromedriver for your version from https://chromedriver.chromium.org/.
    - Unzip and copy Chromedriver or Geckodriver to: /Users/username/PycharmProjects/pytestSelenium_project/venv/bin/chromedriver
----
- Setup virtual environment:
    - Install test requirements (from ~/projects/automations/):
        - pip install -r test-requirements.txt
----

## 02. Brief details about the files and folders

    - pytestSelenium_project:
----
    - directory name: Logs
    - description: used for execution log files
----
    - python package: pageObjects/
    - directory name: folder/
    - description: this folder contains page object file which represents the screens of your web app as a series of objects and encapsulates the features represented by a page.
----
    - directory name: Reports
    - description: this folder contains .html file
----
    - directory name: Screenshot
    - description: saved screenshot for specific scenario
----
    - directory name: TestData
    - description: .xml files
----
    - python package: tests/
    - directory name: conf/
    - file: confing.ini
    - description: this file is common file and contains common fixtures related to test scripts.
----
    - python package: tests/
    - directory name: test_scripts/*.py
    - description: these are our actual automation test script.
----
    - python package: utilities/
    - file: readProerties.py
    - description: this file contains common utility functions.
----
    - directory name: venv
----
## 03. Pytest commands
    - Run specific testcase:
        - pytest -v -s tests/test_scripts/test_login.py
    - Run specific testcase and create html report:
        - pytest -v -s –html=Reports\report.html tests/test_scripts/test_login.py

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
- Elements within of the “key” Element are Child Elements
- Elements placed at the same level side by side are Sibiling Elements
- Remember to use the best locators (never use absolute XPath or absolute CSS).
- ID and data attributes are the best for locating elements.

## 06. Tutorials and useful links

- https://www.selenium.dev/documentation/webdriver/
- https://github.com/nadvolod/selenium-java
- https://www.youtube.com/watch?v=aIfP8rOx66E&t=1825s&ab_channel=UltimateQA
- https://www.youtube.com/watch?v=Xjv1sY630Uc&t=189s&ab_channel=TechWithTim
