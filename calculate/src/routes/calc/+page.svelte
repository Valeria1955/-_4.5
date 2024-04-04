<script>
	// выполняется импорт функции createEventDispatcher
	// из библиотеки svelte, которая позволяет принемать и
	// отправлять пользовательские события / функции
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	let num1 = 0;
	let num2 = 0;
	let action = '+';
	let result = 0;
  
	// выбор оператора, функция действия
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
	  // вызов функции
	  dispatch('calculation', { result });
	}
  </script>
  
  <!-- Секция формы калькулятора -->
  <main class="playground">
	<h1>Детский калькулятор</h1>
	<!-- bind: value={num1}
	привязка переменной и ее значения,
	привязка переменной пиm1 и input-->
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
	  padding: 20px; /* Отступ внутри контейнера */
	  background-color: #f0f8ff; /* Бирюзовый цвет фона */
	  border-radius: 20px; /* Закругление углов */
	}
  
	.input-field, .select-field {
	  margin: 10px;
	  padding: 10px;
	  border: 2px solid #87ceeb; /* Светло-бирюзовая граница */
	  border-radius: 15px; /* Закругление углов */
	  font-size: 18px;
	}
  
	.calculate-btn {
	  background-color: #20b2aa; /* Цвет кнопки - бирюзовый */
	  color: white;
	  padding: 15px;
	  border: none;
	  border-radius: 20px; /* Закругление углов */
	  cursor: pointer;
	  font-size: 20px;
	  transition: background-color 0.3s; /* Плавное изменение цвета фона */
	}
  
	.calculate-btn:hover {
	  background-color: #008080; /* Цвет кнопки при наведении - темно-бирюзовый */
	}
  
	.result {
	  font-size: 30px;
	  color: #2e8b57; /* Цвет результата - зеленый */
	  margin-top: 20px;
	}
  </style>