# Cucumber Tricky Interview Questions and Answers for Lead SDET (10+ Years)

## 1. What is the biggest mistake teams make with Cucumber?
Using Cucumber as a test automation tool instead of a collaboration tool.

Bad:
- UI-centric scenarios
- Click-based steps

Good:
- Business-focused behavior
- Readable by stakeholders

---

## 2. What is wrong with having too many steps in a Scenario?
Problems:
- Hard to maintain
- Poor readability
- Duplicate logic
- Increased execution complexity

Keep scenarios concise and business-oriented.

---

## 3. Difference Between Background and Hooks

### Background
Business preconditions.

Example:
Customer is logged in.

### Hooks
Technical setup and cleanup.

Examples:
- Browser initialization
- Database cleanup
- Test data setup

Rule:
Business Setup → Background
Technical Setup → Hooks

---

## 4. Why avoid UI details in Feature files?
Feature files should describe business behavior, not implementation details.

Bad:
When user clicks submit button

Good:
When customer submits order

---

## 5. What is Scenario Outline?
Used for data-driven testing.

Benefits:
- Reusable scenarios
- Reduced duplication
- Better maintainability

---

## 6. Scenario Outline vs TestNG DataProvider

### Scenario Outline
- Business readable
- Gherkin based

### DataProvider
- Technical implementation
- Java based

Use Scenario Outline when stakeholders need visibility.

---

## 7. What are Hooks?
Hooks execute before or after scenarios.

Common Hooks:
- @Before
- @After
- @BeforeStep
- @AfterStep

Uses:
- Browser launch
- Cleanup
- Reporting

---

## 8. Hook Execution Order

Example:
@Before(order=1)
@Before(order=2)

Lower order executes first.

Execution Flow:
Before → Scenario → After

---

## 9. How do you run specific scenarios?
Use Tags.

Examples:
- @Smoke
- @Regression
- @API
- @UI
- @Critical

---

## 10. Enterprise Tag Strategy

Recommended:
- @Smoke
- @Regression
- @Sanity
- @API
- @UI
- @Critical

Avoid:
- @Test1
- @Test2
- @Test3

---

## 11. How do you share data between steps?

Options:
- PicoContainer
- Dependency Injection
- Scenario Context

Avoid:
- Global variables
- Static variables

---

## 12. Why are static variables dangerous in parallel execution?
Issues:
- Shared state
- Data corruption
- Race conditions

Preferred:
- ThreadLocal
- Scenario Context

---

## 13. How do you handle parallel execution?
Requirements:
- Thread-safe drivers
- Thread-safe context
- No shared mutable state

Tools:
- TestNG
- JUnit
- Maven Surefire

---

## 14. What is a Cucumber Data Table?
Used for structured test data.

Benefits:
- Readability
- Reusability
- Easy maintenance

---

## 15. Data Table vs Scenario Outline

### Data Table
Multiple values within one scenario.

### Scenario Outline
Same scenario executed multiple times.

---

## 16. What is a Doc String?
Used for large text payloads.

Common Use Cases:
- REST API request bodies
- JSON payloads
- XML payloads

---

## 17. How would you integrate Cucumber with REST Assured?
Architecture:
Feature File
→ Step Definitions
→ REST Assured Requests
→ Assertions

Benefits:
- Business-readable API tests
- Better stakeholder collaboration

---

## 18. Why do large Cucumber projects become difficult to maintain?

Reasons:
- Duplicate steps
- Large feature files
- Poor tagging
- UI-centric design
- Tight coupling

Solutions:
- Reusable steps
- Shared context
- Modular design

---

## 19. What reporting tools have you used with Cucumber?

Popular Choices:
- Extent Reports
- Allure Reports
- Cucumber HTML Reports

Report Contents:
- Features
- Scenarios
- Steps
- Screenshots
- Execution Time

---

## 20. How would you design a scalable Cucumber framework?

Suggested Structure:

features/
stepdefinitions/
pages/
api/
hooks/
context/
utils/
runner/
reports/

Best Practices:
- Dependency Injection
- Page Object Model
- ThreadLocal support
- Parallel execution
- CI/CD integration

---

## Executive-Level Question

### When should you NOT use Cucumber?

Avoid Cucumber when:
- Unit testing
- Performance testing
- Infrastructure testing
- No business stakeholder involvement

Cucumber provides the most value when business, QA, and development teams collaborate using shared acceptance criteria.
