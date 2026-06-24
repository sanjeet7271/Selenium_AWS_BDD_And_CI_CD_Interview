# Selenium Coding Interview Questions and Answers for 11+ Years SDET

## 1. Design a Thread-Safe WebDriver Framework

``` java
public class DriverManager {
    private static ThreadLocal<WebDriver> driver = new ThreadLocal<>();

    public static WebDriver getDriver() {
        return driver.get();
    }

    public static void setDriver(WebDriver webDriver) {
        driver.set(webDriver);
    }

    public static void unload() {
        driver.remove();
    }
}
```

**Why not use static WebDriver?** - Static drivers are shared across
threads. - They cause test failures during parallel execution.

------------------------------------------------------------------------

## 2. Build a Generic Explicit Wait Utility

``` java
public static WebElement waitForVisibility(
        WebDriver driver,
        By locator,
        int timeout) {

    WebDriverWait wait =
            new WebDriverWait(
                    driver,
                    Duration.ofSeconds(timeout));

    return wait.until(
            ExpectedConditions
                    .visibilityOfElementLocated(locator));
}
```

------------------------------------------------------------------------

## 3. Build a Generic Click Utility

``` java
public void click(By locator) {
    WebElement element =
            new WebDriverWait(driver, Duration.ofSeconds(10))
            .until(ExpectedConditions.elementToBeClickable(locator));

    element.click();
}
```

------------------------------------------------------------------------

## 4. Handle StaleElementReferenceException

``` java
public void clickWithRetry(By locator) {
    int retries = 3;

    while(retries > 0) {
        try {
            driver.findElement(locator).click();
            return;
        } catch (StaleElementReferenceException e) {
            retries--;
        }
    }
}
```

------------------------------------------------------------------------

## 5. Custom Page Load Wait

``` java
new WebDriverWait(driver, Duration.ofSeconds(30))
    .until(d -> ((JavascriptExecutor)d)
        .executeScript("return document.readyState")
        .equals("complete"));
```

------------------------------------------------------------------------

## 6. Dynamic Web Table Handling

``` java
for(WebElement row : rows){
    if(row.getText().contains("Failed")){
        System.out.println(row.getText());
    }
}
```

------------------------------------------------------------------------

## 7. Multiple Window Handling

``` java
String parent = driver.getWindowHandle();

for(String child : driver.getWindowHandles()) {
    if(!child.equals(parent)) {
        driver.switchTo().window(child);
    }
}
```

------------------------------------------------------------------------

## 8. Screenshot Utility

``` java
File src = ((TakesScreenshot)driver)
    .getScreenshotAs(OutputType.FILE);
```

------------------------------------------------------------------------

## 9. Page Object Model Example

``` java
@FindBy(id="username")
WebElement username;

@FindBy(id="password")
WebElement password;
```

------------------------------------------------------------------------

## 10. Selenium Grid Execution

``` java
WebDriver driver = new RemoteWebDriver(
        new URL(gridUrl),
        options);
```

------------------------------------------------------------------------

# Architect-Level Selenium Questions

## Why do Selenium tests become flaky?

-   Timing issues
-   Dynamic DOM
-   Shared test data
-   Environment instability

### Solutions

-   Explicit waits
-   API-assisted setup
-   Stable locators
-   Test isolation

------------------------------------------------------------------------

## How do you reduce execution time from 6 hours to 45 minutes?

-   Parallel execution
-   Selenium Grid
-   Docker containers
-   Cloud execution
-   Test impact analysis

------------------------------------------------------------------------

## How would you design a framework supporting 10,000 tests?

-   ThreadLocal Driver
-   Retry logic
-   Dynamic suites
-   Distributed execution
-   Centralized reporting

------------------------------------------------------------------------

## Frequently Asked Architect Questions

1.  Explain W3C WebDriver Protocol.
2.  Difference between WebDriver and RemoteWebDriver.
3.  How does Selenium Grid route requests?
4.  How would you implement self-healing locators?
5.  How would you debug intermittent failures?
