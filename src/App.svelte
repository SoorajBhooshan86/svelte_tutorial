<script>
	import ElevatedButton from "./ElevatedButton.svelte";

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

	let people = [
		{ name: "Manu", age: 20, skill: "CSS", id: 1 },
		{ name: "Raj", age: 25, skill: "JavaScript", id: 2 },
		{ name: "Kannan", age: 18, skill: "Dart", id: 3 },
		{ name: "Jazz", age: 6, skill: "Flutter", id: 4 },
	];

	const removePerson = (id) => {
		people = people.filter((person) => person.id != id);
	};
	let showModal = false;

	const toggleModel = () => {
		showModal = !showModal;
	};
</script>

<main>
	<h1 style="color: {bgColor};">Hello {bgColor}!</h1>
	<button on:click={changeColor}>Change color</button>

	both does the same thing on input it will be one way binding, add value and
	then it will be to way binding
	<input type="text" on:input={handleInput} value={bgColor} />
	<input type="text" bind:value={bgColor} />
	<input type="text" bind:value={firstName} />
	<input type="text" bind:value={lastName} />
	<p>{fullName}</p>

	<ElevatedButton text="Life is Hard" {showModal} on:click={toggleModel} />

	{#each people as person (person.id)}
		<div class="info">
			{#if person.skill === "CSS"}
				<p>I am a Pro</p>
			{/if}
			<h3>{person.name}</h3>
			<p>{person.age}</p>
			<button
				on:click={() => {
					removePerson(person.id);
				}}>Delete</button
			>
		</div>
	{:else}
		<p>So sorry,,,, nobodys here</p>
	{/each}

	<button on:click={toggleModel}>Toggle</button>
</main>

<style>
	.info {
		background-color: lightblue;
		padding: 20px;
		margin: 20px;
	}
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
