# Automation Test Framework Architecture

## 1. Framework Architecture

``` text
                         ┌──────────────────────────────────────┐
                         │              CI/CD PIPELINE          │
                         │                                      │
                         │  Git → Jenkins → Maven → TestNG     │
                         │                                      │
                         │  • Code Checkout                     │
                         │  • Build                             │
                         │  • Test Execution                    │
                         │  • Parallel Execution                │
                         │  • Allure Report                     │
                         └──────────────────┬───────────────────┘
                                            │
                                            ▼
                         ┌──────────────────────────────────────┐
                         │          TEST EXECUTION LAYER        │
                         │                                      │
                         │              TestNG.xml              │
                         │                                      │
                         │     Module 1   Module 2   Module 3   │
                         └──────────────────┬───────────────────┘
                                            │
                                            ▼
                         ┌──────────────────────────────────────┐
                         │         PARALLEL EXECUTION           │
                         │                                      │
                         │   Thread 1 → Module 1 Test Cases     │
                         │   Thread 2 → Module 2 Test Cases     │
                         │   Thread 3 → Module 3 Test Cases     │
                         │                                      │
                         │   • Thread-safe execution            │
                         │   • Independent test data            │
                         │   • Independent user credentials     │
                         └──────────────────┬───────────────────┘
                                            │
                                            ▼
                         ┌──────────────────────────────────────┐
                         │            PRECONDITIONS             │
                         │                                      │
                         │ • Login                              │
                         │ • Environment Setup                  │
                         │ • Test Data Setup                    │
                         │ • Read Test Data from JSON           │
                         │ • API-based Setup / Functional Steps │
                         └──────────────────┬───────────────────┘
                                            │
                                            ▼
                         ┌──────────────────────────────────────┐
                         │           BUSINESS LOGIC             │
                         │             TEST CASES               │
                         │                                      │
                         │ Module-wise Business Logic Java      │
                         │ files containing business flows      │
                         └──────────────────┬───────────────────┘
                                            │
                     ┌──────────────────────┼──────────────────────┐
                     │                      │                      │
                     ▼                      ▼                      ▼
              ┌──────────────┐       ┌──────────────┐      ┌──────────────┐
              │  TEST STEPS  │       │  TEST PAGES  │      │  ASSERTIONS  │
              │              │       │              │      │              │
              │ Module-wise  │       │ Page Objects │      │ Module-wise  │
              │ Java files   │       │ Module-wise  │      │ validations  │
              └──────┬───────┘       └──────┬───────┘      └──────┬───────┘
                     │                      │                      │
                     └──────────────────────┼──────────────────────┘
                                            │
                                            ▼
                         ┌──────────────────────────────────────┐
                         │              BASE UI                 │
                         │             BaseUI.java              │
                         │                                      │
                         │ • Browser Setup                      │
                         │ • Driver Management                  │
                         │ • Read Test Data                     │
                         │ • Read User Details                  │
                         │ • Common UI Operations               │
                         │ • Thread-safe Driver Handling        │
                         └──────────────────┬───────────────────┘
                                            │
                                            ▼
                         ┌──────────────────────────────────────┐
                         │             APPLICATION              │
                         │                                      │
                         │             Web Application           │
                         └──────────────────────────────────────┘


 ┌─────────────────────────────────────────────────────────────────────────┐
 │                         TEST DATA LAYER                                 │
 │                                                                         │
 │  ┌─────────────────────┐       ┌─────────────────────────────────────┐ │
 │  │ Test Data JSON      │       │ User Details JSON                   │ │
 │  │                     │       │                                     │ │
 │  │ • Test case data    │       │ • Independent credentials           │ │
 │  │ • Module data       │       │ • User details per test case        │ │
 │  │ • Dynamic data      │       │ • Supports parallel execution       │ │
 │  └─────────────────────┘       └─────────────────────────────────────┘ │
 └─────────────────────────────────────────────────────────────────────────┘


 ┌─────────────────────────────────────────────────────────────────────────┐
 │                        INTEGRATION LAYER                                │
 │                                                                         │
 │  ┌──────────────┐     ┌────────────────┐     ┌────────────────────────┐ │
 │  │ API Steps    │     │ Database       │     │ PDFUtil                │ │
 │  │              │     │ Connection     │     │                        │ │
 │  │ API request  │     │                │     │ Read PDF               │ │
 │  │ & response   │     │ Extract DB     │     │ Extract content        │ │
 │  │ validation   │     │ data           │     │ Verify PDF vs UI       │ │
 │  └──────────────┘     │ Validate UI/   │     └────────────────────────┘ │
 │                       │ API data       │                                 │
 │                       └────────────────┘                                 │
 └─────────────────────────────────────────────────────────────────────────┘


                         ┌──────────────────────────────────────┐
                         │             UTILITIES                │
                         │                                      │
                         │ • Constants                          │
                         │ • Calendar Utility                   │
                         │ • JSON Utility                       │
                         │ • Common Utility                     │
                         │ • Wait/Helper Utility                │
                         │ • Date/Time Utility                  │
                         │ • Other Reusable Components           │
                         └──────────────────┬───────────────────┘
                                            │
                                            ▼
                         ┌──────────────────────────────────────┐
                         │            ALLURE REPORT             │
                         │                                      │
                         │ • Test Results                       │
                         │ • Test Steps                         │
                         │ • Screenshots                        │
                         │ • Logs                               │
                         │ • Failure Details                    │
                         │ • Execution Summary                  │
                         └──────────────────────────────────────┘


                         ┌──────────────────────────────────────┐
                         │       TEST COVERAGE & ENVIRONMENTS   │
                         │                                      │
                         │  REGRESSION          SMOKE           │
                         │      │                 │              │
                         │   ┌──┴──┐          ┌───┼────┐         │
                         │   │     │          │   │    │         │
                         │  DEV   QA         DEV QA  PILOT       │
                         │                                      │
                         └──────────────────────────────────────┘
```

## 2. CI/CD Execution Flow

``` text
Developer
   │
   ▼
Git / Bitbucket
   │
   ▼
Jenkins CI/CD
   │
   ├── Checkout Code
   │
   ├── Maven Build
   │
   ├── Compile
   │
   ├── TestNG Suite Selection
   │
   ├── Environment Selection
   │       ├── DEV
   │       ├── QA
   │       └── PILOT
   │
   ├── Parallel Test Execution
   │       ├── Thread 1 → Module A
   │       ├── Thread 2 → Module B
   │       ├── Thread 3 → Module C
   │       └── Thread 4 → Module D
   │
   ├── API / DB / PDF Validation
   │
   ├── Generate Allure Report
   │
   └── Publish Results
           │
           ├── PASS
           └── FAIL
```

## 3. Parallel Execution Design

The framework supports parallel execution using independent test data,
credentials, and browser sessions.

### Independent User Credentials

``` text
Test Case 1 → User A
Test Case 2 → User B
Test Case 3 → User C
```

This prevents parallel tests from modifying the same user/session.

### Thread-Safe Browser/Driver Management

``` text
Thread 1 → Driver 1 → Test Case 1
Thread 2 → Driver 2 → Test Case 2
Thread 3 → Driver 3 → Test Case 3
```

For Selenium-based execution, `ThreadLocal<WebDriver>` can be used in
`BaseUI` to maintain independent browser sessions per thread.

## 4. Jenkins Parameterization

The CI/CD pipeline can expose runtime parameters such as:

``` text
Jenkins Parameters

Environment:
  DEV / QA / PILOT

Suite:
  Smoke / Regression

Browser:
  Chrome / Edge / Firefox

Execution:
  Parallel / Sequential

Thread Count:
  1 / 2 / 4 / 8
```

This allows the same automation framework to execute different suites
and environments without changing the test code.

## 5. Framework Components

  -----------------------------------------------------------------------
  Component                           Responsibility
  ----------------------------------- -----------------------------------
  **TestNG.xml**                      Module-wise test suite and test
                                      execution configuration

  **Preconditions**                   Login, environment setup, test data
                                      setup, JSON reading and API setup

  **Business Logic**                  Module-wise Java files containing
                                      business-level test flows

  **Test Steps**                      Reusable module-specific UI/API
                                      test steps

  **Test Pages**                      Page Object classes and UI element
                                      interactions

  **Assertions**                      Module-specific validation and
                                      verification logic

  **Test Data JSON**                  Test-case-specific and
                                      module-specific test data

  **User Details JSON**               Independent credentials/user
                                      details for test cases

  **BaseUI.java**                     Browser setup, driver management,
                                      test-data and user-data handling

  **API Steps**                       API requests, responses and API
                                      data validation

  **Database Connection**             Database connectivity, data
                                      extraction and UI/API validation

  **PDFUtil**                         PDF reading, content extraction and
                                      PDF-vs-UI validation

  **Utilities**                       Constants, calendar, JSON, waits
                                      and common reusable utilities

  **Allure Report**                   Test results, steps, screenshots,
                                      logs and failure details

  **Jenkins CI/CD**                   Automated build, test execution and
                                      result publishing

  **Parallel Execution**              Concurrent execution using
                                      independent threads/sessions
  -----------------------------------------------------------------------

## 6. Test Coverage

### Regression Suite

Regression testing is executed in:

-   DEV
-   QA

### Smoke Suite

Smoke testing is executed in:

-   DEV
-   QA
-   PILOT

### Coverage Matrix

  Test Suite     DEV    QA   PILOT
  ------------ ----- ----- -------
  Regression     Yes   Yes      No
  Smoke          Yes   Yes     Yes

## 7. High-Level Architecture

``` text
                         ┌───────────────────┐
                         │   Git / Bitbucket  │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │      Jenkins      │
                         │      CI/CD        │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ Maven + TestNG    │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │ Parallel Execution│
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │   Preconditions   │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │  Business Logic   │
                         └─────────┬─────────┘
                                   │
                 ┌─────────────────┼─────────────────┐
                 ▼                 ▼                 ▼
            Test Steps         Test Pages       Assertions
                 │                 │                 │
                 └─────────────────┼─────────────────┘
                                   │
                                   ▼
                              BaseUI.java
                                   │
                                   ▼
                             Application

       ┌──────────────────────────────────────────────────┐
       │              Supporting Components               │
       │                                                  │
       │ JSON │ API │ Database │ PDF │ Utilities         │
       └──────────────────────┬───────────────────────────┘
                              │
                              ▼
                        Allure Report
```

## 8. Interview Explanation

A concise way to explain this framework in an interview:

> "Our automation framework follows a modular and layered architecture.
> TestNG manages module-wise test execution, while business logic is
> separated from reusable test steps, page objects, and assertions.
> Preconditions handle login, environment setup, test-data creation and
> API-based setup. Test data and user credentials are maintained
> independently in JSON files, which also helps us achieve reliable
> parallel execution.
>
> The framework has reusable API, database and PDF utilities for
> end-to-end validations. BaseUI handles browser and common UI
> operations. The framework is integrated with Jenkins for CI/CD, where
> we can select the environment, suite, browser and thread count through
> parameters. Smoke tests run across DEV, QA and PILOT, while regression
> runs across DEV and QA. Allure is used for execution reporting,
> screenshots, logs and failure analysis." \`\`\`
