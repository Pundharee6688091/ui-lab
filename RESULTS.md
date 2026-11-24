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
- node --version, npm --version and npx cypress version: v24.11.1, 11.6.2 and Cypress 16.2.1 (stable)
- Step 4.3, failure message for the wrong title: Timed out retrying after 10000ms, + expected - actual, -'Web form' (what the page had) +'Web Form' (what the test expected)
- Step 4.6, tool and calories in the answer of POST /api/pizza:
- Step 4.7, the line of the admin list that shows your pizza:
- Step 4.8, run 1, result, duration and pizza name:
- Step 4.8, run 2, result, duration and pizza name:
- Step 4.9 (optional), browser and result:

## Part B
1.
2.
3.
4.
5.
6.
7.
