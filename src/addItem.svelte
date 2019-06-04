<script>
	import { addItem } from './store.svelte'
	let text = ''

	const clickOnButton = () => {
		addItem(text)
		text = ''
	}
</script>

<style>
	.add {
		width: 100%;
		display: flex;
		justify-content: space-between;
	}
	input {
		height: 40px;
		width: 60%;
		margin-right: 10px;
		border: 1px solid purple;
		margin-bottom: 20px;
	}

	.button {
		flex: 1;
		height: 40px;
		border: 1px solid purple;
		border-radius: 3px;
		display: flex;
		align-items: center;
		justify-content: center;
		cursor: pointer;
		color: purple;
		box-sizing: border-box;
	}

	.button:hover {
		background: purple;
		color: #fff;
	}
</style>

<div class="add">
	<input type="text" bind:value={text} placeholder="enter your text" />
	<div class="button" on:click={clickOnButton}>Добавить</div>
</div>
