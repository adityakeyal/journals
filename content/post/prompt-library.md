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

Prompt for performance evaluation:

```
I am preparing for a performance review at my company where my 
work is evaluated against three key attributes: 
Attribute 1, 
Attribute 2, 
Attribute 3 

As part of this process, I need to write a self-assessment that reflects 
my contributions over the last two quarters. I would like this self-assessment to justify a high performance rating. 

To help with this task, I will provide definitions for each of the three attributes and a summary of my projects and contributions. I would like 
you to: 

1. Assign each of my projects to one of the three attributes where it best fits. Please ensure that each project is only assigned once. 

2. Write a positive and detailed self-assessment for each attribute, explaining how my projects demonstrate my proficiency in that area. Include specific examples and details. 

3. Highlight the impact of my work by including quantifiable metrics where possible. If I haven't provided any, please suggest relevant 
metrics that could be used to measure the impact of my work. 

Here are the definitions of the attributes: 
[Insert attribute definitions here] 


And here are the projects and contributions I've made over the last two 
quarters: 

[Insert project summaries and contributions here]

```


Create an onboarding plan for new hires

```
Act as an experienced manager with over 20 years of experience 
helping new hires onboard successfully into their roles as quickly as 
possible. 
I have just started a new job as a KeyAccount_Manager in the 
MicrosoftBing _AdSalesteam, responsible for a portfolio of 50 clients 
in the eCommerce industry, and my key performance indicator is US$ 
10M in revenue this quarter. 
Your task is to generate a 30-60-90 day onboarding plan for me using 
the SMART.framewotk: Specific, Measurable, Achievable, Relevant, 
and Time-Bound. 
Match each goal with a metric so you can objectively measure my 
success. Output in table format 
```


Prepare Social Media Posts:

```
You're a social media manager tasked with sharing long-form content 
on Linkedln, but you've noticed that most people don't engage with 
these posts or click the hyperlinks. 
Creatively condense the below lengthy article into concise, valuable 
summaries that capture the essence of the content and deliver 
immediate value to your audience: 
(paste the article) 
```

Prepare a development plan

```
Construct a detailed 30-60-90 day personal development plan that 
not only focuses on job performance, but also showcases your 
proactive nature and organizational skills using the SMART Framework 
(Specific, Measurable, Actionable, Relevant, and Time-Bound). 
Share your approach. Match each step or goal with a quantifiable 
metric so you can measure success. 
Output in table format. 
```



Template format for coding: 

```
I need to implement [specific functionality] in [programming language].
Key requirements:
1. [Requirement 1]
2. [Requirement 2]
3. [Requirement 3]
Please consider:
- Error handling
- Edge cases
- Performance optimization
- Best practices for [language/framework]
Please do not unnecessarily remove any comments or code.
Generate the code with clear comments explaining the logic.
```

Code for review
```
Please review the following code:
[paste your code]
Consider:
1. Code quality and adherence to best practices
2. Potential bugs or edge cases
3. Performance optimizations
4. Readability and maintainability
5. Any security concerns
Suggest improvements and explain your reasoning for each suggestion.
```

