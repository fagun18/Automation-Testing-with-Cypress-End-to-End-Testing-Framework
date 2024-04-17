# Automation-Testing-with-Cypress-End-to-End-Testing-Framework

# Cypress End-to-End Testing Framework

![Cypress Logo](https://github.com/cypress-io/cypress/raw/develop/cli/icons/icon-128x128.png)

Cypress is a JavaScript-based end-to-end testing framework commonly used for testing web applications. It allows you to write and execute tests in a real browser, providing a way to simulate user interactions and assert expected behaviors.

## Key Features

- Write and execute all types of tests: end-to-end, component, and integration tests.
- Real-time feedback loop: Cypress automatically reloads the application and test runner as you change your test code.
- Intercept and modify network requests and responses for stubbing or mocking API calls.
- Capture screenshots and record videos of test runs.
- Simple setup and easy-to-use test runner interface.

## Project Statistics

- Stars: 45.7K
- Contributors: 472
- Forks: 3.1K
- Releases: 329
- Used by: 1.2M

## Getting Started

### Installation

1. **Create a project folder and open it on your preferred text editor.**

2. **Install Cypress in your project:**

    ```bash
    npm install --save-dev cypress
    ```

3. **Launch the Cypress Test Runner:**

    ```bash
    npx cypress open
    ```

### Running Tests

1. **Select "E2E Testing" in the Cypress Test Runner.**

2. **Choose Chrome as your preferred browser for testing.**

3. **Click "Start E2E Testing in Chrome."**

4. **Create a new test spec and name it.**

5. **Write your test code in the spec file.**

6. **Run the test by clicking on the spec file in the Cypress Test Runner.**

## Example Test

```javascript
/// <reference types="cypress" />

describe("example to-do app", () => {
  beforeEach(() => {
    cy.visit("https://example.cypress.io/todo");
  });

  it("displays two todo items by default", () => {
    cy.get(".todo-list li").should("have.length", 2);
    cy.get(".todo-list li").first().should("have.text", "Pay electric bill");
    cy.get(".todo-list li").last().should("have.text", "Walk the dog");
  });

  it("can add new todo items", () => {
    const newItem = "Feed the cat";

    cy.get("[data-test=new-todo]").type(`${newItem}{enter}`);

    cy.get(".todo-list li")
      .should("have.length", 3)
      .last()
      .should("have.text", newItem);
  });

  it("can check off an item as completed", () => {
    cy.contains("Pay electric bill")
      .parent()
      .find("input[type=checkbox]")
      .check();

    cy.contains("Pay electric bill")
      .parents("li")
      .should("have.class", "completed");
  });
});
```


