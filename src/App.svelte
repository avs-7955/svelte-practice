<script>
	import Modal from "./Modal.svelte"
	import AddPersonForm from "./AddPersonForm.svelte"

	let people = [
		{ name: "yoshi", beltColor: "black", age: 25, id: 1 },
		{ name: "mario", beltColor: "orange", age: 45, id: 2 },
		{ name: "luigi", beltColor: "brown", age: 35, id: 3 },
	]

	let showModal = false

	const toggleModal = () => {
		showModal = !showModal
	}

	const handleClick = (id) => {
		people = people.filter((person) => person.id != id)
	}

	const addPerson = (e) => {
		const per = e.detail
		people = [per, ...people]
		showModal = false
	}
</script>

<Modal isPromo={false} {showModal} on:click={toggleModal}>
	<AddPersonForm on:InsertPerson={addPerson} />
</Modal>

<main>
	<button on:click|once={toggleModal}>Show Modal</button>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColor === "black"}
				<p><strong>MASTER NINJA</strong></p>
			{/if}
			<p>{person.age} years old, {person.beltColor} belt.</p>
			<button on:click={() => handleClick(person.id)}>Delete</button>
		</div>
	{:else}
		<p>There are no people to show...</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
