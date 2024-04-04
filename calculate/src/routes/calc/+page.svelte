<script>
	
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	let num1 = 0;
	let num2 = 0;
	let action = '+';
	let result = 0;
  
	
	function calculate() {
	  switch (action) {
		case '+':
		  result = num1 + num2;
		  break;
		case '-':
		  result = num1 - num2;
		  break;
		case '*':
		  result = num1 * num2;
		  break;
		case '/':
		  result = num1 / num2;
		  break;
	  }
	 
	  dispatch('calculation', { result });
	}
  </script>
  
  
  <main class="playground">
	<h1>Детский калькулятор</h1>
	
	<input type="number" bind:value={num1} placeholder="Введите первое число" class="input-field">
	<select bind:value={action} class="select-field">
	  <option value="+">+</option>
	  <option value="-">-</option>
	  <option value="*">*</option>
	  <option value="/">/</option>
	</select>
	<input type="number" bind:value={num2} placeholder="Введите второе число" class="input-field">
	<button on:click={calculate} class="calculate-btn">Посчитать</button>
   
	{#if result !== ''}
	<p class="result">Результат: {result}</p>
	{/if}
  </main>
  
  <style>
	main.playground {
	  margin-top: 30px;
	  display: flex;
	  flex-direction: column;
	  align-items: center;
	  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.08);
	  padding: 20px; 
	  background-color: #f0f8ff; 
	  border-radius: 20px; 
	}
  
	.input-field, .select-field {
	  margin: 10px;
	  padding: 10px;
	  border: 2px solid #87ceeb; 
	  border-radius: 15px; 
	  font-size: 18px;
	}
  
	.calculate-btn {
	  background-color: #20b2aa; 
	  color: white;
	  padding: 15px;
	  border: none;
	  border-radius: 20px; 
	  cursor: pointer;
	  font-size: 20px;
	  transition: background-color 0.3s; 
	}
  
	.calculate-btn:hover {
	  background-color: #008080; 
	}
  
	.result {
	  font-size: 30px;
	  color: #2e8b57; 
	  margin-top: 20px;
	}
  </style>