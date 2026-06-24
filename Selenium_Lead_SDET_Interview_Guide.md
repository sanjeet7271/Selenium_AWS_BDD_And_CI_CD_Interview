# Selenium Tricky Interview Questions and Answers for Lead SDET (10+ Years)

## 1. Why do Selenium tests become flaky?
Common reasons:
- Poor synchronization
- Dynamic elements
- Network latency
- Hard waits
- Shared test data
- Environment instability

Solution:
Use explicit waits and robust framework design.

---

## 2. Difference Between Implicit and Explicit Wait

### Implicit Wait
- Global wait
- Applies to all elements

### Explicit Wait
- Targeted wait
- Condition-based
- Preferred in enterprise frameworks

---

## 3. Why is mixing Implicit and Explicit Waits dangerous?
Problems:
- Unpredictable execution time
- Longer waits
- Difficult debugging

Best Practice:
Use explicit waits only.

---

## 4. What causes StaleElementReferenceException?
Occurs when:
- DOM refreshes
- Page reloads
- Element reference becomes invalid

Solution:
Re-locate the element before interacting.

---

## 5. How do you handle dynamic web elements?
Use:
- contains()
- starts-with()
- Stable attributes
- Relative locators

Avoid:
- Dynamic IDs

---

## 6. getText() vs getAttribute()

### getText()
Returns visible text.

### getAttribute()
Returns HTML attribute value.

Common Example:
Input fields require getAttribute("value").

---

## 7. Why does getText() return empty?
Possible causes:
- Hidden element
- Input field
- Timing issue
- Shadow DOM

---

## 8. How do you handle Shadow DOM?
Options:
- Selenium 4 Shadow Root APIs
- JavaScriptExecutor

Standard locators may fail.

---

## 9. findElement() vs findElements()

### findElement()
- Returns first match
- Throws NoSuchElementException

### findElements()
- Returns list
- Returns empty list if not found

---

## 10. Handling iFrames

Switch to frame first:

driver.switchTo().frame();

Return:

driver.switchTo().defaultContent();

---

## 11. Why does click() fail?
Reasons:
- Element not visible
- Overlay present
- Synchronization issue
- Element not clickable

---

## 12. Is JavaScript Click a Good Solution?
Use only when necessary.

Pros:
- Bypasses UI restrictions

Cons:
- Does not simulate real user behavior

---

## 13. Actions Class vs JavaScriptExecutor

### Actions
- Simulates user interactions
- Drag and drop
- Hover

### JavaScriptExecutor
- Direct browser manipulation

Preferred:
Actions first.

---

## 14. How do you handle browser downloads?
Configure browser preferences.

Validate:
- File exists
- File size
- File content

---

## 15. How do you handle browser alerts?
Methods:
- accept()
- dismiss()
- getText()

Use:
driver.switchTo().alert();

---

## 16. What causes ElementClickInterceptedException?
Examples:
- Loading spinner
- Popup
- Sticky header
- Animation

Investigate root cause before workaround.

---

## 17. How do you design a scalable Selenium framework?

Suggested Structure:

pages/
tests/
utils/
config/
drivers/
reports/
listeners/

Patterns:
- POM
- Factory
- Builder
- Singleton

---

## 18. How do you run Selenium tests in parallel?

Avoid:
static WebDriver

Use:
ThreadLocal<WebDriver>

Benefits:
- Thread safety
- Better scalability

---

## 19. Selenium Grid 4 vs Grid 3

Grid 4 Benefits:
- Better scalability
- Docker support
- Distributed architecture
- GraphQL support
- Improved observability

---

## 20. How would you reduce a 3-hour Selenium suite to 20 minutes?
Strategies:
- Parallel execution
- Headless execution
- API validation instead of UI
- Remove duplicate tests
- Optimize waits

---

## 21. Why should API tests replace some UI tests?
UI tests are:
- Slower
- More brittle
- More expensive

Testing Pyramid:
Unit Tests
→ API Tests
→ UI Tests

---

## 22. What are Page Object Model limitations?
Problems:
- Large page classes
- Duplicate code
- Maintenance overhead

Solutions:
- Component Objects
- Reusable widgets
- Better abstraction

---

## 23. What metrics do you track?
Examples:
- Execution Time
- Pass Rate
- Flakiness Percentage
- Defect Leakage
- Coverage

---

## 24. Selenium Tests Pass Locally but Fail in Jenkins. Why?
Potential causes:
- Browser version mismatch
- Driver mismatch
- Headless mode differences
- Environment issues
- Timing problems

---

## 25. When should Selenium NOT be used?

Avoid Selenium for:
- API testing
- Database validation
- Performance testing
- Backend verification

Use Selenium for real user workflow validation.

---

## Senior-Level Scenario

### Design an Enterprise Selenium Platform

GitHub
→ Jenkins Pipeline
→ Dockerized Selenium Grid
→ Parallel Execution
→ Allure Reports
→ S3 Storage
→ Slack Notifications

Key Features:
- Thread-safe framework
- Parallel execution
- Retry strategy
- CI/CD integration
- Cross-browser support
- Centralized reporting
