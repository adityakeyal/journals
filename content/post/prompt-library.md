---
title: "Prompt Library"
date: 2025-01-28T17:34:55+05:30
math: false
tags: [genAI]
categories: []
---

Date/time handling has always been messy in code, so I'm letting Claude handle the chaos of parsing freeform scheduling requests and turning them into structured JSON. Did I cover most ways dates and times are mentioned when people schedule meetings?


```
system_prompt = 
Extract all temporal expressions from the text, including partial, informal, or business-context 
information. 
Return them in JSON format as an array of objects: [{"type": "TYPE", "value" : EXTRACTED VALUE", "timezone" "TIMEZONE_IF_SPECIFIED"}]

Types can be: 
- specific_date: Full or partial dates (e g. , '12/25/2024' , 'December 25th", "the 25th , '25/12')
- relative_day: Relative references (e.g., "tomorrow", "day after tomorrow", "next week", "in a few days" ) 
- weekday: Day mentions (e.g., "this coming Monday" , "Monday" "next Tuesday" , "every Friday" , 
- month: Month references (e.g., "in March", "next month", "end of April", "early next month") 
- time: Time mentions (e.g., "at 2pm PST", "morning EST", "afternoon GMT", "first thing , "COB", "EOD") 
- duration: Duration mentions (e.g., "for 2 hours", "30 minutes", "couple of hours", "brief", "quick") 
- period: Time periods (e.g., "this week", "next quarter", "holiday season", "fiscal year", "In couple of hours" 
- preference: Time preferences (e.g., "whenever works", "at your convenience", "when you' re free", "now", "ASAP") 
- recurring: Recurring patterns (e.g., "every other week", "daily" , "weekly" , "monthly" )
- fiscal: Fiscal year references (e.g., Q2 FY25", "FY24" , "fiscal year end" ) 
- cultural: Cultural or seasonal references (e.g., "during Ramadan", "before Christmas", "summer break", "after holidays") 
- milestone: Project-specific milestones (e.g., "after launch", "post-review", "before deployment") 
- business: Business process references (e.g., "after standup", "next sprint", "post-refinement") 

Rules: 
1. Preserve original wording in the 'value' field but convert it to lowercase (retain qualifiers like "early" "late" "every", or "next"). 
2. If multiple temporal expressions are found, return each one as a separate object in the array. 
3. Include timezone in the response when specified (e.g. , "PST", "EST", "GMT", "1ST"). 
4. Distinguish between fiscal and calendar year references. 
5. Handle cultural and seasonal references with appropriate context. 
6. Recognize project and business process milestones. 
```


Prompt to generate test cases: 
```
l. Objective: Develop a suite of unit tests for the function to handle various input scenarios, including both valid and invalid inputs, as if the function is being called from an external client. Refactor the tests to consolidate cormon steps into a single 
meth0d or utility function to enhance code maintainability and readability. 

2. Test File: Create the unit tests in a separate file named test_parsing_operationsl.py. 

3. Test Scenarios: 
- valid Input: Test with a well-formed request containing a valid user query. 
- Invalid Input: Test with an empty request body, malforned JSON, and unexpected data types. 
- Error Handling: Ensure that appropriate error messages and status codes are returned for 
invalid inputs. 
- Test with at least 10 different user queries, with a mix of valid and invalid inputs including special character, escape characters, and edge cases. 

4. Common Steps: 
- Identify and refactor common steps in the test cases into a helper method to avoid redundancy and inprove clarity.

5. Documentation: Document the test results in a table format with the following columns: 
- Request Input: Description of the input used in the test. 
- Response Output: Expected response from the function, including Status, code and message. 

6. Output: The code should record the tests and print out the table as output of the test 
suite run. Additionally, save the results to an Excel file with formatted tables and word 
wrapping for better readability. 
7. Example Results Table Format: 
| Request Input | Response Output |
|-----------------------------------|
| Valid JSON with query | {"status": "success", "UserQuery" : "example" } | 
| Empty request body | {"status": "error", "message" : "Empty request body" } | 
| Malformed JSON | {"status": "error", "message" : "JSON decode error " } | 
| Unexpected data type | {"status": "error", "message": "Error processing request"} | 

8. Tools and Libraries: 
- use unittest for creating and running the tests. 
- Use pandas and openpyxl for saving results to an Excel file. 
- Use tabulate for printing the results table to the console
```


A simple prompt to upgrade the quality of any piece of code you write.

```
Make this code more resilient, readable and maintainable by incorporating: 
Error handling with specific status codes 
JSON response format 
Logging for debugging 
Input validation 
Clear function documentation 
Separation of concerns 
Proper type hints 
```

