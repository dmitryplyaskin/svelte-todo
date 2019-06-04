<script>
	import { removeItem, compliteItem } from './store.svelte'
	export let data
</script>

<style>
	.item {
		box-sizing: border-box;
		width: 100%;
		border-bottom: 1px solid rgb(185, 5, 185);
		padding: 0 20px 10px;
		margin-bottom: 10px;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.text {
		color: purple;
	}

	.complite {
		position: relative;
	}
	.complite::before {
		content: '';
		width: 120%;
		height: 1px;
		background: purple;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
	}

	.check,
	.notcheck {
		width: 10px;
		height: 10px;
		cursor: pointer;
		border: 1px solid rgb(185, 5, 185);
	}

	.check {
		background: rgb(185, 5, 185);
	}

	.delete {
		width: 10px;
		height: 10px;
		position: relative;
		cursor: pointer;
	}
	.f,
	.s {
		position: absolute;
		left: 50%;
		top: 50%;
		width: 20px;
		height: 2px;
		background: red;
		border-radius: 3px;
	}

	.f {
		transform: translate(-50%, -50%) rotate(45deg);
	}
	.s {
		transform: translate(-50%, -50%) rotate(-45deg);
	}
</style>

<div class="item">
	<div
		class={data.complite ? 'check' : 'notcheck'}
		on:click={() => compliteItem(data.id)} />
	<div class={`text ${data.complite && `complite`} `}>{data.name}</div>
	<div class="delete" on:click={() => removeItem(data.id)}>
		<div class="f" />
		<div class="s" />
	</div>
</div>
