Functional Programming is a popular approach to software development. In Functional Programming, developers organize code into smaller functions, then combine those functions to build complex programs.

In this spreadsheet application project, you'll learn about parsing and evaluating mathematical expressions, implementing spreadsheet functions, handling cell references, and creating interactive web interfaces. You'll learn how to dynamically update the page based on user input.

This project will cover concepts like the map() method, find() method, parseInt(), the includes() method.

######################################################################################################################################################################
Sure, let's walk through your code step-by-step to understand what it does:

### 1. Arithmetic Functions
```javascript
const infixToFunction = {
  "+": (x, y) => x + y,
  "-": (x, y) => x - y,
  "*": (x, y) => x * y,
  "/": (x, y) => x / y,
};
```
- This object maps arithmetic operators to their corresponding functions, enabling the evaluation of infix expressions (e.g., `2 + 3`).

### 2. Infix Evaluation
```javascript
const infixEval = (str, regex) => str.replace(regex, (_match, arg1, operator, arg2) => infixToFunction[operator](parseFloat(arg1), parseFloat(arg2)));
```
- This function takes a string `str` and a regular expression `regex`, replaces matches in the string with their evaluated results using the `infixToFunction` object.

### 3. High Precedence Evaluation
```javascript
const highPrecedence = str => {
  const regex = /([\d.]+)([*\/])([\d.]+)/;
  const str2 = infixEval(str, regex);
  return str === str2 ? str : highPrecedence(str2);
};
```
- This function ensures multiplication and division are evaluated before addition and subtraction by recursively applying `infixEval` until no changes are made.

### 4. Helper Functions
```javascript
const isEven = num => num % 2 === 0;
const sum = nums => nums.reduce((acc, el) => acc + el, 0);
const average = nums => sum(nums) / nums.length;
```
- These functions provide basic utilities like checking if a number is even, calculating the sum, and finding the average of an array of numbers.

### 5. Median Calculation
```javascript
const median = nums => {
  const sorted = nums.slice().sort((a, b) => a - b);
  const length = sorted.length;
  const middle = length / 2 - 1;
  return isEven(length)
    ? average([sorted[middle], sorted[middle + 1]])
    : sorted[Math.ceil(middle)];
};
```
- This function calculates the median of an array of numbers, handling both odd and even lengths appropriately.

### 6. Spreadsheet Functions
```javascript
const spreadsheetFunctions = {
  sum,
  average,
  median,
  even: nums => nums.filter(isEven),
  someeven: nums => nums.some(isEven),
  everyeven: nums => nums.every(isEven),
  firsttwo: nums => nums.slice(0, 2),
  lasttwo: nums => nums.slice(-2),
  has2: nums => nums.includes(2),
  increment: nums => nums.map(num => num + 1),
  random: ([x, y]) => Math.floor(Math.random() * y + x),
  range: nums => range(...nums),
  nodupes: nums => [...new Set(nums).values()],
  "": arg => arg // Empty string property that returns its argument
};
```
- This object contains various utility functions for common spreadsheet operations like filtering even numbers, summing, averaging, and more.

### 7. Applying Functions
```javascript
const applyFunction = str => {
  const noHigh = highPrecedence(str);
  const infix = /([\d.]+)([+-])([\d.]+)/;
  const str2 = infixEval(noHigh, infix);
  const functionCall = /([a-z0-9]*)\(([0-9., ]*)\)(?!.*\()/i;
  const toNumberList = args => args.split(",").map(parseFloat);
  const apply = (fn, args) => spreadsheetFunctions[fn.toLowerCase()](toNumberList(args));
  return str2.replace(functionCall, (match, fn, args) => spreadsheetFunctions.hasOwnProperty(fn.toLowerCase()) ? apply(fn, args) : match);
};
```
- This function processes a string to evaluate all recognized functions and arithmetic operations within it.

### 8. Range and Character Utilities
```javascript
const range = (start, end) => Array(end - start + 1).fill(start).map((element, index) => element + index);
const charRange = (start, end) => range(start.charCodeAt(0), end.charCodeAt(0)).map(code => String.fromCharCode(code));
```
- These functions generate arrays of numbers and characters, useful for handling ranges in spreadsheet formulas.

### 9. Formula Evaluation in Context
```javascript
const evalFormula = (x, cells) => {
  const idToText = id => cells.find(cell => cell.id === id).value;
  const rangeRegex = /([A-J])([1-9][0-9]?):([A-J])([1-9][0-9]?)/gi;
  const rangeFromString = (num1, num2) => range(parseInt(num1), parseInt(num2));
  const elemValue = num => character => idToText(character + num);
  const addCharacters = character1 => character2 => num => charRange(character1, character2).map(elemValue(num));
  const rangeExpanded = x.replace(rangeRegex, (_match, char1, num1, char2, num2) => rangeFromString(num1, num2).map(addCharacters(char1)(char2)));
  const cellRegex = /[A-J][1-9][0-9]?/gi;
  const cellExpanded = rangeExpanded.replace(cellRegex, match => idToText(match.toUpperCase()));
  const functionExpanded = applyFunction(cellExpanded);
  return functionExpanded === x ? functionExpanded : evalFormula(functionExpanded, cells);
};
```
- This function evaluates formulas in a string, expanding cell references and ranges, and applying functions recursively.

### 10. DOM Manipulation on Load
```javascript
window.onload = () => {
  const container = document.getElementById("container");
  const createLabel = (name) => {
    const label = document.createElement("div");
    label.className = "label";
    label.textContent = name;
    container.appendChild(label);
  };
  const letters = charRange("A", "J");
  letters.forEach(createLabel);
  range(1, 99).forEach(number => {
    createLabel(number);
    letters.forEach(letter => {
      const input = document.createElement("input");
      input.type = "text";
      input.id = letter + number;
      input.ariaLabel = letter + number;
      input.onchange = update;
      container.appendChild(input);
    });
  });
};
```
- This code creates a grid of input fields for a 10x99 spreadsheet, labeling rows with numbers and columns with letters.

### 11. Update Function
```javascript
const update = event => {
  const element = event.target;
  const value = element.value.replace(/\s/g, "");
  if (!value.includes(element.id) && value.startsWith('=')) {
    element.value = evalFormula(value.slice(1), Array.from(document.getElementById("container").children));
  }
};
```
- This function handles input changes, evaluating the formula if it starts with `=`, and updating the cell with the computed result.

### Summary
- **Grid Creation**: Dynamically creates a 10x99 spreadsheet grid with input fields.
- **Formula Parsing**: Parses and evaluates arithmetic and function-based formulas within input fields.
- **Range Handling**: Expands cell ranges and replaces cell references with actual values.
- **Event Handling**: Updates cell values based on user input, evaluating formulas and handling circular references.

This code effectively creates a simple, interactive spreadsheet application within a web page. If you have any further questions or need specific details, feel free to ask!