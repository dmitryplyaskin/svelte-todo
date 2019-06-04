<script context="module">
	import effector from 'effector/effector.umd.js'

	const randomId = () => Math.random() * 100000

	const addItem = effector.createEvent()
	const compliteItem = effector.createEvent()
	const removeItem = effector.createEvent()

	const initialStore = [{ name: 'First item', complite: false, id: randomId() }]
	const store = effector.createStore(initialStore)

	store
		.on(addItem, (state, name) => [
			...state,
			{
				name,
				id: randomId(),
				complite: false,
			},
		])
		.on(compliteItem, (state, id) =>
			state.map(x => {
				if (x.id === id && !x.complite) {
					return {
						...x,
						complite: true,
					}
				}
				return x
			})
		)
		.on(removeItem, (state, id) => state.filter(x => x.id !== id))

	export { store, addItem, removeItem, compliteItem }
</script>
