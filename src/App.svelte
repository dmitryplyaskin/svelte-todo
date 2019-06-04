<script>
	import { store } from './store.svelte'
	import Item from './item.svelte'
	import Add from './addItem.svelte'
</script>

<style>
	.main {
		width: 500px;
		background: #fff;
		box-shadow: 0 0 12px rgba(0, 0, 0, 0.1);
		margin: 40px auto;
		padding: 20px;
		border-radius: 3px;
	}
</style>

<div class="main">
	<Add />
	{#each $store as item (item.id)}
		<Item data={item} />
	{/each}
</div>
