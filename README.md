# ui-lab

Part 2 (Selenium WebDriver in Java) and Part 4 (Cypress).

## selenium-java/ (Part 2)

Maven project with JUnit tests for Selenium's web form and for QP-01, written once directly (`QP01Test`) and once with page objects (`QP01PageObjectTest`). Screenshots of a run are saved in `screenshots/` and a Maven report in `reports/`.

Needs Java 21 or newer, Maven, Chrome and the `CHROMEDRIVER` variable (the path of ChromeDriver, see Part 0 of the lab). Run all tests from the `selenium-java` folder:

```
mvn test -Dheadless=true
```

## cypress/ (Part 4)

Cypress project with a spec for Selenium's web form (`web-form.cy.js`) and a spec for QP-01 (`pizza-scenario.cy.js`) that uses a custom command `adminLogin`. The videos and screenshots of a full run are saved in `cypress/videos` and `cypress/screenshots`.

Needs Node.js 22 or newer and Chrome. Run all specs from the `cypress` folder:

```
npm install
npx cypress run --browser chrome
```

`npm install` is needed only the first time.
