<script>
	import Header from './Header.svelte';
	import './styles.css';
  </script>
  
  <div class="app">
	<Header />
  
	<main>
	  <slot />
	</main>
  
	<footer>
	  <p>Посетите <a href="https://kit.svelte.d­ev">kit.svelte.dev</a>, чтобы узнать о SvelteKit</p>
	</footer>
  </div>
  
  <style>
	.app {
	  display: flex;
	  flex-direction: column;
	  min-height: 100vh;
	  background-color: #fdf5e6; 
	}
  
	main {
	  flex: 1;
	  display: flex;
	  flex-direction: column;
	  padding: 1rem;
	  width: 100%;
	  max-width: 64rem;
	  margin: 0 auto;
	  box-sizing: border-box;
	}
  
	footer {
	  display: flex;
	  flex-direction: column;
	  justify-content: center;
	  align-items: center;
	  padding: 12px;
	  background-color: #ffe4b5;
	  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); 
	}
  
	footer a {
	  font-weight: bold;
	  color: #4169e1; 
	  text-decoration: none;
	  transition: color 0.3s; 
	}
  
	footer a:hover {
	  color: #000080; 
	}
  
	@media (min-width: 480px) {
	  footer {
		padding: 12px 0;
	  }
	}
  </style>