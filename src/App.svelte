<script>
	let name = "Stupid";
	let bgColor = "red";
	let firstName = "Jack";
	let lastName = "Sparrow";
	$: fullName = firstName + " " + lastName;

	$: {
		console.log(fullName);
		console.log(bgColor);
	}

	const changeColor = () => {
		bgColor = "yellow";
	};

	const handleInput = (e) => {
		bgColor = e.target.value;
	};
</script>

<main>
	<h1 style="color: {bgColor};">Hello {bgColor}!</h1>
	<button on:click={changeColor}>Change color</button>
	<!-- both does the same thing -->
	<!-- on input it will be one way binding, add value and then it will be to way binding -->
	<!-- <input type="text" on:input={handleInput} value={bgColor} /> -->
	<input type="text" bind:value={bgColor} />
	<input type="text" bind:value={firstName} />
	<input type="text" bind:value={lastName} />
	<p>{fullName}</p>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		background-color: azure;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
