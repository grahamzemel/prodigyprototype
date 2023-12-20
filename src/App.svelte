<script>
	import "./main.scss";
	import { currentView } from "./store/states.js";
	import Home from './main/Home.svelte';
	import Login from './main/Login.svelte';
	import { onMount } from 'svelte';

	onMount(() => {
	//   const storedUser = localStorage.getItem('user');
	//   const storedKey = localStorage.getItem('key');
	//   if (storedUser && storedKey) {
	// 	user.set(storedUser);
	// 	key.set(storedKey);
		currentView.set('chat');
	//   }
	});
	// Function to change views
	function navigate(view) {
	  currentView.set(view);
	}
  
</script>
<div style="text-align:center;">
	<h1 class="title is-2" style="padding-top:1rem;">Prodigy (Prototype)</h1>
	<h3 class="title is-4">Created by <a href="https://grahamzemel.com" style="text-decoration:none;">Graham Zemel</a></h3>
	<!-- <h5 class="title is-6">View the source code <a href="https://github.com/grahamzemel" style="text-decoration:none;">here</a>!</h5> -->
	</div>
	{#if $currentView === 'login'}
	<Login/>
  {:else if $currentView === 'chat'}
	<Home/>
  {/if}