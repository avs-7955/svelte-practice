<script>
	import { createEventDispatcher } from "svelte"
	let name
	let beltColor
	let age // svelte will store the value in int not string.

	// for checkboxes
	let skills = []

	const dispatch = createEventDispatcher()

	const handleSubmit = () => {
		const person = {
			name,
			beltColor,
			age,
			skills,
			id: Math.random(),
		}
		dispatch("InsertPerson", person)
	}
</script>

<form on:submit|preventDefault={handleSubmit}>
	<input type="text" placeholder="Name" bind:value={name} />
	<input type="number" placeholder="Age" bind:value={age} />

	<label>Skills:</label>
	<input type="checkbox" bind:group={skills} value="fighting" /> fighting
	<br />
	<input type="checkbox" bind:group={skills} value="running" />running <br />
	<input type="checkbox" bind:group={skills} value="sneaking" /> sneaking
	<br />

	<label>Beltcolor:</label>
	<select bind:value={beltColor}>
		<option value="black">black</option>
		<option value="white">white</option>
		<option value="brown">brown</option>
		<option value="orange">orange</option>
	</select>

	<button>Add person</button>
</form>

<style>
</style>
