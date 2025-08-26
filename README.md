# simplecalculator-activity
NAME-KIRUPASAGAR S
REGISTER NUMBER-212224230126
```
--- index.html ---
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Simple Calculator</title>
<link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="calculator">
        <h1>Simple Calculator</h1>
        <div class="input-group">
            <label for="number1">First Number:</label>
            <input type="number" id="number1" placeholder="Enter first number" step="any">
        </div>
        <div class="input-group">
            <label for="number2">Second Number:</label>
            <input type="number" id="number2" placeholder="Enter second number" step="any">
        </div>
        <div class="operation-group">
            <label>Choose Operation:</label>
            <div class="operation-buttons">
                <button class="operation-btn" data-operation="add">➕ Add</button>
                <button class="operation-btn" data-operation="subtract">➖ Subtract</button>
                <button class="operation-btn" data-operation="multiply">✖️ Multiply</button>
                <button class="operation-btn" data-operation="divide">➗ Divide</button>
            </div>
        </div>
        <button class="calculate-btn" onclick="calculate()">Calculate Result</button>
        <div class="result">
            <span class="result-text" id="resultText">Select an operation and click Calculate to see the result</span>
        </div>
    </div>
<script src="script.js"></script>
</body>
</html>

--- styles.css ---
*
{
margin:0;
padding:0;
box-sizing:border-box;
}
body
{
font-family:'Segoe UI',Tahoma,Geneva,Verdana,sans-serif;
background:linear-gradient(135deg,#e74c3c 0%,#c0392b 100%);
min-height:100vh;
display:flex;
justify-content:center;
align-items:center;
padding:20px;
}
.calculator
{
background:#fff;
padding:40px;
border-radius:20px;
box-shadow:0 20px 40px rgba(0,0,0,.1);
max-width:400px;
width:100%;
}
.calculator h1
{
text-align:center;
color:#333;
margin-bottom:30px;
font-size:2rem;
font-weight:600;
}
.input-group
{
margin-bottom:20px;
}
.input-group label
{
display:block;
margin-bottom:8px;
color:#555;
font-weight:500;
}
.input-group input
{
width:100%;
padding:12px 16px;
border:2px solid #e1e5e9;
border-radius:10px;
font-size:16px;
transition:border-color .3s;
}
.input-group input:focus
{
outline:none;
border-color:#e74c3c;
}
.operation-group
{
margin-bottom:25px;
}
.operation-group label
{
display:block;
margin-bottom:12px;
color:#555;
font-weight:500;
}
.operation-buttons
{
display:grid;
grid-template-columns:1fr 1fr;
gap:10px;
}
.operation-btn
{
padding:12px 20px;
border:2px solid #e1e5e9;
background:#fff;
border-radius:10px;
cursor:pointer;
font-size:16px;
font-weight:500;
transition:all .3s;
color:#555;
}
.operation-btn:hover
{
border-color:#e74c3c;
background:#fdf2f2;
}
.operation-btn.active
{
background:#e74c3c;
border-color:#e74c3c;
color:#fff;
}
.calculate-btn
{
width:100%;
padding:15px;
background:linear-gradient(135deg,#e74c3c 0%,#c0392b 100%);
color:#fff;
border:none;
border-radius:10px;
font-size:18px;
font-weight:600;
cursor:pointer;
transition:transform .2s;
margin-bottom:20px;
}
.calculate-btn:hover
{
transform:translateY(-2px);
}
.calculate-btn:active
{
transform:translateY(0);
}
.result
{
background:#fdf2f2;
padding:20px;
border-radius:10px;
border-left:4px solid #e74c3c;
min-height:60px;
display:flex;
align-items:center;
}
.result-text
{
font-size:18px;
color:#333;
font-weight:500;
}
.result-value
{
font-size:24px;
color:#e74c3c;
font-weight:700;
margin-left:10px;
}
.error
{
color:#e74c3c;
}
@media(max-width:480px)
{
.calculator
{
padding:30px 20px;
}
.calculator h1
{
font-size:1.5rem;
}
.operation-buttons
{
grid-template-columns:1fr;
}
}

--- script.js ---
let selectedOperation=null;
document.querySelectorAll('.operation-btn').forEach(btn=>{
btn.addEventListener('click',function(){
document.querySelectorAll('.operation-btn').forEach(b=>b.classList.remove('active'));
this.classList.add('active');
selectedOperation=this.dataset.operation;
});
});
document.querySelectorAll('input').forEach(input=>{
input.addEventListener('keypress',function(e){
if(e.key==='Enter')
{
calculate();
}
});
});
function calculate()
{
const num1=parseFloat(document.getElementById('number1').value);
const num2=parseFloat(document.getElementById('number2').value);
const resultText=document.getElementById('resultText');
if(isNaN(num1)||isNaN(num2))
{
resultText.innerHTML='<span class="error">⚠️ Please enter valid numbers</span>';
return;
}
if(!selectedOperation)
{
resultText.innerHTML='<span class="error">⚠️ Please select an operation</span>';
return;
}
let result;
let operationSymbol;
switch(selectedOperation)
{
case'add':
result=num1+num2;
operationSymbol='+';
break;
case'subtract':
result=num1-num2;
operationSymbol='-';
break;
case'multiply':
result=num1*num2;
operationSymbol='×';
break;
case'divide':
if(num2===0)
{
resultText.innerHTML='<span class="error">⚠️ Cannot divide by zero</span>';
return;
}
result=num1/num2;
operationSymbol='÷';
break;
default:
resultText.innerHTML='<span class="error">⚠️ Invalid operation</span>';
return;
}
const formattedResult=Number.isInteger(result)?result:result.toFixed(6).replace(/\.?0+$/,'');
resultText.innerHTML=`<span class="result-text">${num1} ${operationSymbol} ${num2} = </span><span class="result-value">${formattedResult}</span>`;
}
document.querySelectorAll('input').forEach(input=>{
input.addEventListener('input',function(){
document.getElementById('resultText').textContent='Select an operation and click Calculate to see the result';
});
});
```
# output
<img width="1916" height="1195" alt="Screenshot 2025-08-26 172710" src="https://github.com/user-attachments/assets/77eb47c7-69a3-48f0-bce4-8d5575ad6989" />
<img width="1919" height="1199" alt="Screenshot 2025-08-26 173503" src="https://github.com/user-attachments/assets/aceb19db-b6e9-4a0b-813d-8ce728ead6de" />
<img width="1919" height="1199" alt="Screenshot 2025-08-26 173514" src="https://github.com/user-attachments/assets/3dd2e48c-3a62-4917-9a9b-71fc97aff9d2" />
<img width="1919" height="1199" alt="Screenshot 2025-08-26 173534" src="https://github.com/user-attachments/assets/b256568c-d2d6-4b46-be07-abbf9cd7f361" />

