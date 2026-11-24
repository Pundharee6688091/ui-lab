# UI lab results

Tool parts that I chose: Part 2 (Selenium WebDriver in Java) and Part 4 (Cypress)

## Part 0
- Step 0.1, Chrome version: 158.0.8127.37 (Official Build) (arm64)
- Step 0.3, ChromeDriver version: ChromeDriver 158.0.8127.37
- Step 0.4, locator of Pizza, Please!: $$("button[name='pizza-please']")
- Step 0.4, locator of Excluded tools: $x("//label[normalize-space()='Excluded tools']/following-sibling::select")
- Step 0.4, locator of Must be vegetarian: $$("#default-checkbox")
- Step 0.4, locator of Custom Pizza Name: $$("input#pizza-name")
- Step 0.5, pizza name, tool and calories of the run by hand: Lab Pizza 20261124-100128, Pizza cutter, 425 calories per slice

| Step | Actual result | Pass or fail |
|------|---------------|--------------|
| 1    | The heading "Looking to break out of your pizza routine?" was shown | Pass |
| 2    | Max Calories per Slice, Excluded tools, Must be vegetarian and Custom Pizza Name appeared | Pass |
| 3    | The fields showed 600, Knife, vegetarian ticked and Lab Pizza 20261124-100128 | Pass |
| 4    | Name Lab Pizza 20261124-100128, tool Pizza cutter (not Knife), 425 calories per slice (600 or fewer) | Pass |
| 5    | "Please log in first." msg pop up | Pass |
| 6    | The page showed "Latest pizza recommendations" | Pass |
| 7    | The line "Lab Pizza 20261124-100128 (tool=Pizza cutter, ingredients_number=5)" was in the list | Pass |

## Part 2: Selenium WebDriver in Java
- Step 2.4, the failure line for the wrong title: 
`[ERROR]   FirstTest.webFormOpens:20 expected: <Web Form> but was: <Web form>`
- Step 2.15, QP01Test run 1, result and time: Pass, 11.968 s
- Step 2.15, QP01Test run 2, result and time: Pass, 11.759 s
- Step 2.20, full run 1, time and number of tests: 32.058 s, 5 tests, all passed
- Step 2.20, full run 2, time and number of tests: 24.731 s, 5 tests, all passed

## Part 4: Cypress
- node --version, npm --version and npx cypress version: v24.11.1, 11.6.2 and 16.3.0 (I upgraded from 16.2.1 to 16.3.0, because with Chrome 158 the second spec of one `npx cypress run` stopped with `* is not a valid URL`)
- Step 4.3, failure message for the wrong title: Timed out retrying after 10000ms, + expected - actual, -'Web form' (what the page had) +'Web Form' (what the test expected)
- Step 4.6, tool and calories in the answer of POST /api/pizza: tool Knife, calories 650
- Step 4.7, the line of the admin list that shows your pizza: `Lab Pizza 20261124-122453 (tool=Scissors, ingredients_number=7)`
- Step 4.8, run 1, result, duration and pizza name: All specs passed (2 of 2), 00:14 (pizza-scenario 00:12, web-form 00:02), pizza Lab Pizza 20261124-122416
- Step 4.8, run 2, result, duration and pizza name: All specs passed (2 of 2), 00:13 (pizza-scenario 00:11, web-form 00:01), pizza Lab Pizza 20261124-122453
- Step 4.9 (optional), browser and result:

## Part B
1. The three number boxes share the id `floating_filled`, so the id cannot pick one box. I would give each box its own id, such as `max-calories`.
2. It is a consistency check. It would catch a server that saves or shows a different tool than the one it recommended.
3. I would check that every ingredient is vegetarian. The page shows only names, but the answer of POST /api/pizza has `vegetarian` for each ingredient, so Cypress can read `response.body` with `cy.intercept`.
4. In Java I had to write every wait myself, and `findElement` without a wait failed with `NoSuchElementException`. Cypress waits by itself, because each `cy.get` and `should` retries for up to 10 seconds. QP-01 was quicker to write in Cypress, and its video and screenshots were easier to read than Maven's text report.
5. I would choose Selenium WebDriver. The page objects keep locators in one place, as our group's UI tests do. Cypress also gave me trouble: with Chrome 158 it crashed on the second spec of a run, and I had to upgrade it to 16.3.0.
6. In `QP01Test` I would change the XPath written in the test, and in every other test that copies it. In `QP01PageObjectTest` I would change only the constant `MAX_CALORIES` in `HomePage.java`. The tests call methods like `setMaxCalories(600)` and never see a locator, so one line repairs them all.
7. Cypress clears the cookies before each test, and QuickPizza uses a cookie to keep a browser on one server. If steps 6 and 7 were a second test, the admin page could come from a server that never saw my pizza, and step 7 would fail. The alias `tool` and the variable `pizzaName` would also be lost.
