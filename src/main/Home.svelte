<script>
	let user = "Webmaster";
	function handleSubmit() {
		console.log("success");
	}
</script>

<div class="columns">
	<div class="column">
		<h1 class="title">Hello {user}!</h1>
		<h1 class="subtitle">Graham Zemel</h1>
	</div>
	<div class="column">
		<input type="text" class="text" bind:value={user} />
		<button class="button is-info"> Bulma </button>
	</div>
</div>
