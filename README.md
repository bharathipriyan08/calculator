# Description:
The calculator webpage is designed with simplicity and functionality in mind. It features a centered layout on the viewport, ensuring readability and accessibility across different devices. The main structure consists of a .calculator div, which encapsulates a display area (#display) showing the current input or result. Below the display, the .buttons div organizes calculator buttons using CSS Grid with three columns (grid-template-columns: repeat(3, 1fr)) for optimal arrangement. Each button (<button>) is styled with uniform padding, background colors indicating different types of operators (+, -, *, /), and transitions on hover for visual feedback (transition: background-color 0.3s). The overall design employs a dark theme (background-color: #333) with contrasting elements for clarity (color: #fff), enhancing usability and ensuring a cohesive user experience when performing arithmetic operations or interacting with the calculator functions.

# Program;
 ```
index.html

<!DOCTYPE html>
<html lang="en">
<head>
    
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Calculator</title>
<link rel="stylesheet" href="styles.css">

</head>
<body>
    
<div class="calculator">
  <div class="display" id="display">0</div>
  <div class="buttons">
    <button class="coperator" onclick="clearDisplay()">C</button>
    <button class="coperator" onclick="backspace()">←</button>
    <button class="operator" onclick="appendOperator('/')">÷</button>
        <button class="operator" onclick="appendOperator('*')">x</button>

    <button onclick="appendDigit('7')">7</button>
    <button onclick="appendDigit('8')">8</button>
    <button onclick="appendDigit('9')">9</button>
    <button class="operator" onclick="appendOperator('-')">-</button>
    <button onclick="appendDigit('4')">4</button>

    <button onclick="appendDigit('5')">5</button>
    <button onclick="appendDigit('6')">6</button>
    <button class="operator" onclick="appendOperator('+')">+</button>
    <button onclick="appendDigit('1')">1</button>
    <button onclick="appendDigit('2')">2</button>
    <button onclick="appendDigit('3')">3</button>
    <button class="operator" onclick="calculate()">%</button>

    <button onclick="appendDigit('0')">0</button>
    <button onclick="appendDecimal('.')">.</button>
    <button class="equaloperator" onclick="calculate()">=</button>


    
    
  </div>
</div>

<script src="script.js"></script>
</body>
</html>


CSS


body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  background-image: url(https://www.shutterstock.com/shutterstock/videos/1093451077/thumb/1.jpg?ip=x480);
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  
}

.calculator {
  width: 300px;
  background-color: #333;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  overflow: hidden;
}

.display {
  height: 80px;
  background-color: #666;
  color: #fff;
  font-size: 2em;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 0 10px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}

button {
  background-color: #eee;
  border: none;
  border-radius: 0;
  cursor: pointer;
  font-size: 1.5em;
  padding: 20px 0;
  transition: background-color 0.3s;
}
.equaloperator {
  grid-column: span 2; 
  background-color: #201e24;
  color: #fff;
}
.coperator {
  background-color: #201e24;
  color: #fff;
}

button:hover {
  background-color: #410cb5;
}

.operator {
  background-color: #ff9500;
  color: #fff;
}

.operator:hover {
  background-color: #ffad33;
}

JS

let displayValue = '0';
let operator = '';
let operand1 = null;
let operand2 = null;
let result = null;

function updateDisplay() {
  const display = document.getElementById('display');
  display.textContent = displayValue;
}

function clearDisplay() {
  displayValue = '0';
  operand1 = null;
  operand2 = null;
  operator = '';
  result = null;
  updateDisplay();
}

function backspace() {
  if (displayValue.length === 1) {
    displayValue = '0';
  } else {
    displayValue = displayValue.slice(0, -1);
  }
  updateDisplay();
}

function appendDigit(digit) {
  if (displayValue === '0' || operator === '=') {
    displayValue = digit;
  } else {
    displayValue += digit;
  }
  updateDisplay();
}

function appendDecimal() {
  if (!displayValue.includes('.')) {
    displayValue += '.';
  }
  updateDisplay();
}

function appendOperator(op) {
  if (operator !== '') {
    calculate();
  }
  operand1 = parseFloat(displayValue);
  operator = op;
  displayValue = '0';
  updateDisplay();
}

function calculate() {
  operand2 = parseFloat(displayValue);
  switch (operator) {
    case '+':
      result = operand1 + operand2;
      break;
    case '-':
      result = operand1 - operand2;
      break;
    case '*':
      result = operand1 * operand2;
      break;
    case '/':
      result = operand1 / operand2;
      break;
    default:
      result = operand2;
  }
  displayValue = result.toString();
  operator = '=';
  updateDisplay();
}
```
# OUTPUT:
![Screenshot (11)](https://github.com/bharathipriyan08/calculator/assets/113762012/38773563-2732-4e37-bdc1-0550c34fde0d)
