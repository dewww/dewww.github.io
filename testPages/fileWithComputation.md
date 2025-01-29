# Interactive Sum Calculator

Enter two numbers and see the sum instantly.

<form oninput="result.value = parseFloat(num1.value || 0) + parseFloat(num2.value || 0)">
  <label>Number 1: <input type="number" id="num1" name="num1" value="0"></label>
  <br>
  <label>Number 2: <input type="number" id="num2" name="num2" value="0"></label>
  <br>
  <label>Sum: <output name="result">0</output></label>
</form>