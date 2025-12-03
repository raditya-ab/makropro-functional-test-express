# makropro-functional-test-express

An Express.js skeleton for MakroPro's functional test assessment.

## Overview

This is a technical assessment to evaluate your problem-solving skills and ability to create RESTful APIs using Express.js. You will need to choose ONE problem from the list below and implement a complete solution.

## Assessment Rules & Guidelines

### ⚠️ Important Restrictions

1. **NO AI-Powered Tools**: You are strictly prohibited from using any AI-powered coding assistants including but not limited to:
   - GitHub Copilot
   - ChatGPT
   - Claude
   - Any other AI code generation tools

2. **NO Built-in Array Methods**: For array manipulation problems, you must write your logic from scratch. The following methods are **NOT ALLOWED**:
   - `sort()`
   - `map()`
   - `filter()`
   - `reduce()`
   - `forEach()`
   - Any other built-in array methods unless explicitly stated in the problem instructions

3. **NO External Helper Libraries**: You are prohibited from using any helper functions or utility libraries (e.g., Lodash, Ramda) unless explicitly allowed by the interviewer.

### 📋 Assessment Approach

1. **Solution First**: Focus on solving the algorithmic problem first. Write and test your core logic function separately before integrating it with the API.

2. **Then API Integration**: Once your solution is working correctly, integrate it into an Express.js API endpoint.

3. **Folder Structure**: Follow common Express.js conventions:
```
   project-root/
   ├── src/
   │   ├── controllers/
   │   ├── routes/
   │   ├── services/
   │   └── utils/
   ├── tests/
   ├── app.js
   ├── server.js
   └── package.json
```

### 📝 Deliverables

- Working Express.js API with at least one endpoint that solves your chosen problem
- Clean, readable code with appropriate error handling
- Basic input validation

---

## Problems (Choose ONE)

### 1. Dutch Flag Problem

**Description**: Given an array consisting of only 0s, 1s, and 2s, rearrange the elements so that all 0s come first, followed by 1s, and then 2s.

**Constraints**:
- You must write your own sorting logic from scratch
- Built-in array methods like `sort()`, `map()`, `filter()` are **NOT ALLOWED**

**Example**:
```javascript
// Input:  [2, 0, 1, 2, 0, 1]  
// Output: [0, 0, 1, 1, 2, 2]
```

**API Endpoint Specification**:
- Method: `POST`
- Path: `/api/dutch-flag`
- Request Body: 
```json
  {
    "array": [2, 0, 1, 2, 0, 1]
  }
```
- Response:
```json
  {
    "input": [2, 0, 1, 2, 0, 1],
    "output": [0, 0, 1, 1, 2, 2]
  }
```

---

### 2. Sort Array by Occurrence

**Description**: Sort the given array based on the frequency of each number, with numbers appearing more frequently placed first. If two numbers have the same frequency, sort them in ascending order.

**Constraints**:
- You must write your own sorting and counting logic from scratch
- Built-in array methods like `sort()`, `map()`, `filter()` are **NOT ALLOWED**

**Example**:
```javascript
// Input:  [0, 0, 8, 4, 5, 6, 5, 4, 3, 3, 1]
// Output: [0, 0, 3, 3, 4, 4, 5, 5, 1, 6, 8]
// Explanation: 0 appears 2x, 3 appears 2x, 4 appears 2x, 5 appears 2x, 
//              1 appears 1x, 6 appears 1x, 8 appears 1x
//              Same frequency numbers are sorted in ascending order
```

**API Endpoint Specification**:
- Method: `POST`
- Path: `/api/sort-by-occurrence`
- Request Body: 
```json
  {
    "array": [0, 0, 8, 4, 5, 6, 5, 4, 3, 3, 1]
  }
```
- Response:
```json
  {
    "input": [0, 0, 8, 4, 5, 6, 5, 4, 3, 3, 1],
    "output": [0, 0, 3, 3, 4, 4, 5, 5, 1, 6, 8]
  }
```

---

### 3. Find the Longest Consecutive Sequence

**Description**: Given an unsorted array of numbers, determine the length of the longest consecutive sequence (a sequence where each number increases by 1).

**Rules**:
- The sequence must consist of consecutive numbers increasing by exactly 1
- The numbers do not have to be in order in the original array
- If there are duplicates, they should be ignored when forming a sequence

**Examples**:
```javascript
// Example 1
const input = [100, 4, 200, 1, 3, 2];
const output = 4; // The sequence is [1, 2, 3, 4]

// Example 2
const input = [0, -1, 1, 2];
const output = 4; // The sequence is [-1, 0, 1, 2]

// Example 3
const input = [];
const output = 0;

// Example 4
const input = [1];
const output = 1;

// Example 5
const input = [1, 1, 3];
const output = 1; // Duplicates are ignored
```

**API Endpoint Specification**:
- Method: `POST`
- Path: `/api/longest-consecutive`
- Request Body: 
```json
  {
    "array": [100, 4, 200, 1, 3, 2]
  }
```
- Response:
```json
  {
    "input": [100, 4, 200, 1, 3, 2],
    "longestSequenceLength": 4,
    "sequence": [1, 2, 3, 4]
  }
```

---

### 4. Flatten a Deeply Nested Object

**Description**: Create a function that flattens a deeply nested object using dot notation for keys.

**Example**:
```javascript
// Input
{
  a: 1,
  b: {
    c: 2,
    d: {
      e: 3,
      f: {
        g: 4
      }
    }
  },
  h: 5
}

// Output
{
  'a': 1,
  'b.c': 2,
  'b.d.e': 3,
  'b.d.f.g': 4,
  'h': 5
}
```

**API Endpoint Specification**:
- Method: `POST`
- Path: `/api/flatten-object`
- Request Body: 
```json
  {
    "object": {
      "a": 1,
      "b": {
        "c": 2,
        "d": {
          "e": 3
        }
      }
    }
  }
```
- Response:
```json
  {
    "input": { "a": 1, "b": { "c": 2, "d": { "e": 3 } } },
    "output": { "a": 1, "b.c": 2, "b.d.e": 3 }
  }
```

---

### 5. Item Stock Forecast

**Description**: Create a function that forecasts item stock for the next 12 months based on monthly loss and restock percentages.

**Function Signature**:
```javascript
/**
 * Forecasts item stock for the next 12 months
 * 
 * @param {Object} input
 * @param {number} input.initialStock - Initial stock amount
 * @param {number} input.monthlyLossPercentage - Loss percentage per month (applied after restock)
 * @param {number} input.monthlyRestockPercentage - Restock percentage per month
 * @returns {Array} Forecast report for 12 months
 */
```

**Calculation Logic**:
For each month:
1. Start with initial stock
2. Apply restock
3. Apply loss
4. The result is the end of month stock
5. This becomes the initial stock for the next month

**Example**:
```javascript
// Input
{
  initialStock: 100,
  monthlyLossPercentage: 0.05,
  monthlyRestockPercentage: 0.1
}

// Expected Output (first 3 months shown)
[
  {
    "month": 1,
    "initialStock": 100,
    "monthlyLossPercentage": 0.05,
    "monthlyRestockPercentage": 0.1,
    "endOfMonthStock": 104.5
  },
  {
    "month": 2,
    "initialStock": 104.5,
    "monthlyLossPercentage": 0.05,
    "monthlyRestockPercentage": 0.1,
    "endOfMonthStock": 109.2225
  },
  {
    "month": 3,
    "initialStock": 109.2225,
    "monthlyLossPercentage": 0.05,
    "monthlyRestockPercentage": 0.1,
    "endOfMonthStock": 114.18311
  }
  // ... continues for 12 months total
]
```

**API Endpoint Specification**:
- Method: `POST`
- Path: `/api/stock-forecast`
- Request Body: 
```json
  {
    "initialStock": 100,
    "monthlyLossPercentage": 0.05,
    "monthlyRestockPercentage": 0.1
  }
```
- Response:
```json
  {
    "forecast": [
      { "month": 1, "initialStock": 100, "endOfMonthStock": 104.5, ... },
      { "month": 2, "initialStock": 104.5, "endOfMonthStock": 109.2225, ... },
      ...
    ]
  }
```

---

## Evaluation Criteria

Your solution will be evaluated based on:

1. **Correctness**: Does the solution produce the correct output for all test cases?
2. **Code Quality**: Is the code clean, readable, and well-organized?
3. **Algorithm Efficiency**: Is the solution reasonably efficient?
4. **Error Handling**: Are edge cases and errors handled appropriately?
5. **API Design**: Is the API endpoint well-designed and follows REST conventions?
6. **Documentation**: Is the code and API properly documented?

## Getting Started

1. Clone this repository
2. Run `npm install`
3. Choose ONE problem from the list above
4. Implement your solution
5. Test thoroughly
6. Document your work

Good luck! 🚀