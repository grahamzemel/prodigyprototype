<script>
	import { state } from "../store/states.js";
	import { createEventDispatcher } from "svelte";
	import Docs from "./Docs.svelte";
	import Home from "./Home.svelte";

	function setHome(event) {
		state.update((n) => [{ id: 0, component: Home }]);
	}

	function setDocs(event) {
		state.update((n) => [{ id: 0, component: Docs }]);
	}
</script>

<nav class="navbar" role="navigation" aria-label="main navigation">
	<div class="navbar-brand">
		<a class="navbar-item" href="https://bulma.io">
			<img
				alt="img"
				src="https://bulma.io/images/bulma-logo.png"
				width="112"
				height="28"
			/>
		</a>

		<a
			href="javascript:void(0);"
			role="button"
			class="navbar-burger burger"
			aria-label="menu"
			aria-expanded="false"
			data-target="navbarBasicExample"
		>
			<span />
			<span />
			<span />
		</a>
	</div>

	<div id="navbarBasicExample" class="navbar-menu">
		<div class="navbar-start">
			<a
				href="javascript:void(0);"
				class="navbar-item"
				on:click={setHome}
			>
				Home
			</a>

			<a
				href="javascript:void(0);"
				class="navbar-item"
				on:click={setDocs}
			>
				Documentation
			</a>

			<div class="navbar-item has-dropdown is-hoverable">
				<a href="javascript:void(0);" class="navbar-link"> More </a>

				<div class="navbar-dropdown">
					<a href="javascript:void(0);">Navbaritem</a>
				</div>
			</div>
		</div>
	</div>
	<a class="navbar-item" href="https://svelte.dev">
		<img
			alt="img"
			src="https://svelte.dev/svelte-logo-horizontal.svg"
			width="112"
			height="28"
		/>
	</a>
</nav>
