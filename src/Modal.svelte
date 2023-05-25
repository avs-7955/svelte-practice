<script>
	export let isPromo = false
	export let showModal = false
</script>

{#if showModal}
	<div class="backdrop" class:promo={isPromo} on:click|self>
		<div class="modal">
			<slot />
		</div>
	</div>
{/if}

<style>
	.backdrop {
		background-color: rgba(0, 0, 0, 0.8);
		width: 100%;
		height: 100%;
		position: fixed;
	}
	.modal {
		background: white;
		width: 70%;
		/* max-width: 400px; */
		text-align: center;
		padding: 10px;
		border-radius: 15px;
		max-width: 400px;
		margin: 10% auto;
	}
	.promo .modal {
		background: crimson;
		color: white;
	}
</style>
