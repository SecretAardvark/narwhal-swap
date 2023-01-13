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

	export let currentToken = 'Select Token';

	const toggleMenu = () => {
		menuOpen = !menuOpen;
	};
	const setToken = (menuItem) => {
		currentToken = menuItem.name;
		menuOpen = !menuOpen;
	};
</script>

<div class="tokenInput">
	<input type="number" class="amount" />

	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div
		class="token"
		id="token"
		on:click={() => {
			toggleMenu();
		}}
	>
		{currentToken}
	</div>
</div>

{#if menuOpen}
	<div class="tokenMenu">
		{#each tokenList as menuItem}
			<a href="#" on:click={() => setToken(menuItem)}>{menuItem.name}</a>
		{/each}
	</div>
{/if}

<style>
	.tokenMenu {
		background-color: antiquewhite;
		height: 200px;
		width: 85%;
		overflow-y: auto;
		list-style: none;
		position: absolute;
		top: 42px;
		left: 34px;
	}
	.tokenMenu a {
		color: black;
		width: 100%;
		text-decoration: none;
		display: block;
		padding-left: 5px;
	}
	.tokenMenu a:hover {
		background-color: #ccc;
	}
	.token {
		border: 1px solid black;
		width: 85%;
		justify-content: center;
		margin: auto;
	}
	.tokenInput {
		width: 85%;
		background-color: antiquewhite;
	}
</style>
