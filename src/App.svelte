<script>
	import "./main.scss";
	import { state } from "./store/states.js";
	import Navbar from "./main/Navbar.svelte";
	import Home from "./main/Home.svelte";
	import Docs from "./main/Docs.svelte";

	let page 
    $: if ($state) {
        page = $state[0].component.name;
    }
</script>

<Navbar />

<body class="container">
	{#if page == "Home"}
		<Home />
	{/if}
	{#if page == "Docs"}
		<Docs />
	{/if}
</body>
