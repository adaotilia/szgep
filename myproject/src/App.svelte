<script>
  let currentInput = "";
  let result = "";

  function appendValue(value) {
    currentInput += value;
  }

  function calculate() {
    try {
      result = eval(currentInput); 
    } catch (error) {
      result = "Error";
    }
  }

  function clearInput() {
    currentInput = "";
    result = "";
  }
</script>

<div class="calculator">
  <div class="display">
    <div>{currentInput || "0"}</div>
    <div><strong>{result}</strong></div>
  </div>

  <div class="buttons">
    {#each ["7", "8", "9", "4", "5", "6", "1", "2", "3", "0", ".", "/"] as value}
      <button on:click={() => appendValue(value)}>{value}</button>
    {/each}
    {#each ["+", "-", "*", "="] as op}
      <button on:click={op === "=" ? calculate : () => appendValue(op)}>{op}</button>
    {/each}
    <button class="wide" on:click={clearInput}>Clear</button>
  </div>
</div>

<style>
  .calculator {
    max-width: 1000px; 
    max-height: 600px;
    margin: 10px auto;
    padding: 10px;
    border: 2px solid #000000;
    border-radius: 8px;
    text-align: center;
    font-family: Arial, Helvetica, sans-serif
  }

  .display {
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #000000;
    border-radius: 5px;
    font-size: 40px;
    color: rgb(0, 0, 0);
    min-height: 40px;
    background-color: #e576bb;
  }

  .buttons {
    display: grid;
    grid-template-columns: repeat(3, 3fr);
    gap: 20px;
  }

  button {
    padding: 10px;
    font-size: 35px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background-color: #d11997;
    color: rgb(0, 0, 0);
  }

  .wide {
    grid-column: span 2;
  }
</style>
