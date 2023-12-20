<script>
	import { createEventDispatcher } from "svelte";
	const dispatch = createEventDispatcher();

	let username = "";
	let password = "";

	async function login() {
		const response = await fetch(process.env.LOGIN, {
			method: "POST",
			headers: {
				"Content-Type": "application/json",
			},
			body: JSON.stringify({ username, password }),
		});
		if (response.ok) {
			const data = await response.json();
			user.set(data.username);
			localStorage.setItem("user", data.username);
			localStorage.setItem("key", data.key_hex);
			dispatch("login", { username: data.username, key: data.key_hex });
			currentView.set("chat");
			window.location.reload();
			
		} else {
			console.error("Login failed");
			// Handle error
			document.getElementById("login_fail").innerHTML =
				"Login failed, please (1) input a valid username and (2) generate a new key or input a valid key.";
			document.getElementById("login_fail").style.color = "red";
			document.getElementById("login_fail").style.fontSize = "16px";
			setTimeout(function () {
				document.getElementById("login_fail").innerHTML = "";
			}, 5000);
		}
	}

	// async function generateKey() {
	// 	const response = await fetch(process.env.REQUESTKEY, {
	// 		method: "POST",
	// 	});
	// 	const data = await response.text();
	// 	password = JSON.parse(data).key; // Store the generated key in the password variable
	// 	// parse for regular display, 'key' is the key in json
	// 	keyData = password;
	// 	document.getElementById("notification").style.display = "block";
	// 	key.set(password);
	// }
</script>

<div class="section">
	<div id="main" class="container box" style="max-width:40%;">
		<h2 class="title is-2 login-title">Login</h2>
		<!-- <p>Please log in to access the chat room functionality and read about beginner-level quantum mechanics as well as quantum key distribution applications.</p> -->
		<br>
		<div class="rows">
			<div class="row">
				<div class="columns" style="text-align:center;justify-content:center;">
					<div class="column" style="max-width:33%;">
						<p class="label">Username</p>
						<div class="control login-input">
							<input
								class="input"
								type="text"
								bind:value={username}
								placeholder="Ex. Bob, H4CK3R, Turtle123"
							/>
						</div>
					</div>
					<div class="column" style="max-width:33%;">
						<p class="label">Password</p>
						<div class="control login-input">
							<input
								class="input"
								type="password"
								bind:value={password}
								placeholder="Ex. 0842fcb3d..."
							/>
						</div>
					</div>
				</div>
			</div>
			<div class="row" style="text-align:center;">
				<p id="login_fail"></p>
				</div>
			<br>
			<div class="row">
				<div class="columns is-mobile is-vcentered">
					<div class="column is-half">
					  <button class="button is-medium is-link" on:click={login}>
						Login
					  </button>
					</div>
					<!-- <div class="column is-half has-text-right">
					  <button class="button is-medium is-info" on:click={generateKey}>
						Generate Key
					  </button>
					</div> -->
				  </div>
			</div>
		</div>

		
		<!-- <div class="notification key-notification" id="notification">
			<p>
				<strong>Key:</strong> <span class="key">{keyData}</span>
			</p>
			<p>Don't lose it!</p>
		</div> -->
	</div>
</div>
