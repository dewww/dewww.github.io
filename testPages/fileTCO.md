# Interactive Budget Calculator

Enter numbers in the table below. The sum of each column updates automatically.

<form oninput="updateSums()">
  <table border="1" style="border-collapse: collapse; width: 100%; text-align: center;">
    <thead>
      <tr>
        <th>Label</th>
        <th>Option 1</th>
        <th>Option 2</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Initial</strong></td>
        <td><input type="number" class="col1" value="0"></td>
        <td><input type="number" class="col2" value="0"></td>
      </tr>
      <tr>
        <td><strong>Year 1</strong></td>
        <td><input type="number" class="col1" value="0"></td>
        <td><input type="number" class="col2" value="0"></td>
      </tr>
      <tr>
        <td><strong>Year 2</strong></td>
        <td><input type="number" class="col1" value="0"></td>
        <td><input type="number" class="col2" value="0"></td>
      </tr>
      <tr>
        <td><strong>Year 3</strong></td>
        <td><input type="number" class="col1" value="0"></td>
        <td><input type="number" class="col2" value="0"></td>
      </tr>
      <tr>
        <td><strong>Sunset</strong></td>
        <td><input type="number" class="col1" value="0"></td>
        <td><input type="number" class="col2" value="0"></td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td><strong>Sum</strong></td>
        <td><strong><output id="sum1">0</output></strong></td>
        <td><strong><output id="sum2">0</output></strong></td>
      </tr>
    </tfoot>
  </table>
</form>

<script>
function updateSums() {
    let col1Total = 0, col2Total = 0;
    
    document.querySelectorAll('.col1').forEach(input => {
        col1Total += parseFloat(input.value) || 0;
    });

    document.querySelectorAll('.col2').forEach(input => {
        col2Total += parseFloat(input.value) || 0;
    });

    document.getElementById('sum1').value = col1Total;
    document.getElementById('sum2').value = col2Total;
}

// Initialize sums on page load
updateSums();
</script>