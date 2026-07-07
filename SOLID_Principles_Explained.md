# SOLID Principles Explained (Java + Selenium Framework Perspective)

## What is SOLID?

SOLID is a set of 5 Object-Oriented Design principles introduced by
**Robert C. Martin (Uncle Bob)**.

These principles help developers write code that is:

-   Easy to maintain
-   Easy to extend
-   Less coupled
-   Reusable
-   Easy to test

### SOLID Acronym

-   **S** → Single Responsibility Principle
-   **O** → Open/Closed Principle
-   **L** → Liskov Substitution Principle
-   **I** → Interface Segregation Principle
-   **D** → Dependency Inversion Principle

------------------------------------------------------------------------

# 1. Single Responsibility Principle (SRP)

## Definition

> A class should have only one reason to change.

### Bad Example

``` java
class Login {
    public void login() {}
    public void takeScreenshot() {}
    public void sendEmail() {}
    public void generateReport() {}
}
```

This class handles multiple responsibilities.

### Good Example

``` java
class LoginService {
    public void login() {}
}

class ScreenshotService {
    public void takeScreenshot() {}
}

class EmailService {
    public void sendEmail() {}
}

class ReportService {
    public void generateReport() {}
}
```

### Automation Framework Example

Instead of mixing login, DB, reporting, and screenshots in one class,
create:

-   LoginPage
-   DBUtil
-   ReportUtil
-   ScreenshotUtil

------------------------------------------------------------------------

# 2. Open/Closed Principle (OCP)

## Definition

> Software should be open for extension but closed for modification.

### Bad Example

``` java
class Browser {
    public void launch(String browser) {
        if(browser.equals("chrome"))
            System.out.println("Chrome");
        else if(browser.equals("firefox"))
            System.out.println("Firefox");
    }
}
```

Adding a new browser requires modifying existing code.

### Good Example

``` java
interface Browser {
    void launch();
}

class Chrome implements Browser {
    public void launch() {
        System.out.println("Chrome");
    }
}

class Firefox implements Browser {
    public void launch() {
        System.out.println("Firefox");
    }
}
```

Now you can add Edge, Safari, etc. without changing existing classes.

### Selenium Example

Use a `BrowserFactory` instead of `if-else` browser selection.

------------------------------------------------------------------------

# 3. Liskov Substitution Principle (LSP)

## Definition

> A child class should be able to replace its parent class without
> breaking the application.

### Good Example

``` java
class Animal {
    void eat() {}
}

class Dog extends Animal {
    void eat() {}
}
```

### Bad Example

``` java
class Bird {
    void fly() {}
}

class Penguin extends Bird {
    void fly() {
        throw new UnsupportedOperationException();
    }
}
```

A penguin cannot behave like a flying bird.

### Selenium Example

All page classes extending `BasePage` should behave consistently as
`BasePage`.

------------------------------------------------------------------------

# 4. Interface Segregation Principle (ISP)

## Definition

> Clients should not be forced to implement methods they do not use.

### Bad Example

``` java
interface Vehicle {
    void drive();
    void fly();
    void sail();
}
```

### Good Example

``` java
interface Driveable {}
interface Flyable {}
interface Sailable {}
```

Now:

-   Car → Driveable
-   Boat → Sailable
-   Plane → Driveable + Flyable

### Selenium Example

Create smaller interfaces such as:

-   Clickable
-   Typeable
-   Uploadable

instead of one large interface.

------------------------------------------------------------------------

# 5. Dependency Inversion Principle (DIP)

## Definition

> Depend on abstractions, not on concrete implementations.

### Bad Example

``` java
class Login {
    ChromeDriver driver = new ChromeDriver();
}
```

### Good Example

``` java
WebDriver driver;
driver = DriverFactory.getDriver();
```

This allows switching between:

-   Chrome
-   Firefox
-   Edge
-   Selenium Grid

without changing business logic.

------------------------------------------------------------------------

# SOLID in a Selenium Automation Framework

A typical framework structure:

``` text
Tests
   |
Page Objects
   |
Service Layer
   |
Utilities
   |
Driver Factory
   |
WebDriver
```

  Principle   Framework Usage
  ----------- ----------------------------------------------
  SRP         Each page object handles one feature
  OCP         Add browsers without modifying existing code
  LSP         All pages behave as BasePage
  ISP         Small focused interfaces
  DIP         Depend on WebDriver abstraction

------------------------------------------------------------------------

# Interview Answer (Lead SDET)

> "In our Selenium framework, we followed SOLID principles extensively.
> Each page object had a single responsibility (SRP). Browser support
> was implemented through a factory pattern, allowing new browsers to be
> added without changing existing code (OCP). All page objects extended
> a common BasePage (LSP). We used focused interfaces for different
> actions (ISP). Finally, we depended on the WebDriver abstraction and
> used a driver factory instead of creating concrete driver instances
> directly (DIP). This made the framework easier to maintain, extend,
> and test."

------------------------------------------------------------------------

# Important Interview Tip

SOLID principles are commonly used together with design patterns such
as:

-   Factory Pattern
-   Page Object Model (POM)
-   Singleton Pattern
-   Builder Pattern
-   Strategy Pattern

For a Lead SDET role, explaining how SOLID improves framework
scalability and maintainability creates a strong interview impression.
