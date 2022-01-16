### QA Automation Framework Setup
# Python + SeleniumBase

**Pre-Requisites:**

- Make sure you have access to git repo: (https://git.nosolutions.rs/)
- Make sure you have ssh access to your account and key is already added for account.
- Install PyCharm

## 01. Installation steps

- Create a new project in PyCharm
  - Within your terminal navigate to: C:/Users/Username/Documents/TestingProjects/PycharmProjects/
  - Clone project repository: git clone https://git.nosolutions.rs/vladan.furman/onboarding-selenium.git
- Setup Virtual Environment within Pycharm
- Install [Python](https://www.python.org/downloads/) 
- Install SeleniumBaseIO (https://seleniumbase.io/)
  - Open terminal and type: 
    - pip3 install seleniumbase
    - seleniumbase (or sbase) (to check if the installation is passed)
- Install [ChromeDriver](https://chromedriver.chromium.org/) 
  - Open terminal and type:
    - sbase install chromedriver latest, or
    - sbase install chromedriver 97.0.4692.71

## 02. SeleniumBase commands
- Run all tests:
  - pytest
- Run specific testcase and generate html report:
  - pytest -k test_home
  
## 03. Brief details about the files and folders

- pythonSeleniumBase (root folder)
  - custom_screenshots (This folder contains screenshots)
  - data (This folder contains data: .png, .jpeg...)
  - latest_logs (This folder contains: test_info.txt, page_source_info.html, and screenshot.png)
  - page_objects (This Python Package folder contains page object file which represents the screens of your web app as a series of objects and encapsulates the features represented by a page.)
  - tests (This Python Package folder contains automation test script)
  - venvs (This folder contains all dependencies in our virtual environment)
  - report.html (This file is report)
  - requirements.txt (This file represent all dependencies we use)

## 04. Tutorials and useful links

- https://www.youtube.com/watch?v=D0-QGMacMxA&list=PLGLlPuoTA3DURLLEpkJJmN7wXgGztfIo3&index=5&ab_channel=AutomationBro-DilpreetJohal

