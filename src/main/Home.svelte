<script>
// call api on localhost:3000
let words = [];
async function getWords() {
	const response = await fetch("http://localhost:3000/generateCrossword", {
		method: "GET",
	});
	if (response.ok) {
		const data = await response.json();
		words = data.suggestions;
		console.log(words)
	} else {
		console.error("Failed to get words");
	}
}

</script>
<div class="section">
	<div id="main" class="container box">
		<h2 class="title is-3">Prodigy (Prototype)</h2>
		<div class="block">
			<p>
				Prodigy is a prototype of a quantum chat application. It is a
				proof of concept for a quantum key distribution (QKD)
				application that uses the BB84 protocol to generate a shared key
				between two users. The key is then used to encrypt and decrypt
				messages sent between the two users.
			</p>
		</div>
		<button class="button" on:click={getWords}>Get Words</button>
		<div class="block">
			{#each words as word}
			<p>{word}</p>	
			{/each}
		</div>
		<div class="block"></div>
	</div>
</div>
