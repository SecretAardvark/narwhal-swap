<script>
	let menuOpen = false;

	let tokenList = [
		{ name: 'Yada Yada token', price: 100 },
		{ name: 'Lorem Ipsum coin', price: 500 },
		{ name: 'Ethereum', price: 1250 },
		{ name: 'chain link', price: 7 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 },
		{ name: 'filler coin', price: 69 }
	];

	export let token = tokenList[0].name;

	const toggleMenu = () => {
		menuOpen = !menuOpen;
	};
	const setToken = (menuItem) => {
		token = menuItem.name;
		menuOpen = !menuOpen;
	};
</script>

<div
	class="token"
	id="token"
	on:click={() => {
		toggleMenu();
	}}
>
	{token}
</div>
{#if menuOpen}
	<div id="tokenMenu">
		{#each tokenList as menuItem}
			<a href="#" on:click={() => setToken(menuItem)}>{menuItem.name}</a>
		{/each}
	</div>
{/if}
