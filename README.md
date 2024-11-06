# Project Setup

This document provides instructions for setting up the project with Playwright, configuring environment variables using dotenv, and running tests.

## Installation

1. **Clone the Git Repository:** 

    ```bash
    git clone <repository-url>
    cd <repository-name>
    ```
2. **Install Playwright:**

    ```bash
    npm init playwright@latest
    ```
3. **Install Dotenv:**

    ```bash
    npm i dotenv
    ```
## Setting up Environment Variables

1. Rename the **.dummy-env** file to **.env**
2. Add your Trello credentials, key and token to the file.

    ```
    API_KEY=your_trello_api_key
    API_TOKEN=your_trello_token
    TRELLO_EMAIL=your_trello_email
    TRELLO_PASSWORD=your_trello_password
    ```

## Running Test:

1. Run Tests in Headless mode:

    ```bash
    npx playwright test 
        or
    npm run runTest-headless
    ```
2. Run Tests in Headed
    ```bash
    npx playwright test --headed
        or
    npm run runTest-headed
    ```


# Test Details:

### Why the tests?
- The test cases check basic functionality of a Trello Board.
- The actions covered in the test cases cover different set of UI elements, performing assertions and verify the changes are being reflected on the UI.

### Before Setup:
- In the before setup I am initializing API context and using API functions to create a Task Board with lists "To-Do", "In-Progress", "Done"
- Logging in using UI functions and then storing the session state in a state.json file at runtime, this helps us avoid logging in before running every test case.

### Test 1 - Add Tasks in To-Do List
- First test case covers adding tasks Task #1, Task #2 and Task #3 to the list.
- Asserting that every task is added to the list using expect.

### Test 2 - Drag and Drop Task from one List to other Lists.
- Verify a Task#2 and Task#3 are in the To-Do list.
- Drag and Drop tasks to In-Progress and Done List.
- Assert tasks are shown in the correct list and negative assertion to check they are not in the To-Do list.

### Test 3 - Create a Template for Task
- Click the create template button and add the template with template name.
- Edit the template and add a "Green" label to the template.
- Edit the template and add a "Checklist" to the template.

### Test 4 - Create a task from Template and add Edit checklist in the task
- Click the created template and click on the "Create Task from Template" button.
- Verify the created task.
- Mark the checklist item 2 as done.
- Verify the checklist item is marked as done.

### After Setup:
- Logout using UI function
- Delete the created Task board using API function.

### CI Setup:
- A basic CI is setup to run whenever a change is pushed in the repository.
- The test results are stored as artifacts and can be found under the test run.