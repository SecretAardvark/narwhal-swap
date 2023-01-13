<script>
	// @ts-nocheck

	let menuOpen = false;
	//might need this to fix the border issue?
	// let focused = false;

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
	export let amount = 0;
	export let id;

	const toggleMenu = () => {
		menuOpen = !menuOpen;
	};
	const setToken = (menuItem) => {
		currentToken = menuItem.name;
		menuOpen = !menuOpen;
	};
	const setAmount = () => {
		amount = document.getElementById(id).value;
	};
</script>

<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
<div class="tokenInput" tabindex="0">
	<input type="number" {id} class="amount" on:input={() => setAmount()} />

	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div
		class={currentToken === 'Select Token' ? 'tokenDefault' : 'tokenDefault tokenSelected'}
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
	.tokenDefault {
		display: flex;
		/* border: 1px solid black; */
		width: 30%;
		height: 35%;
		padding: 10px;
		border-radius: 15px;
		justify-content: center;
		margin: auto;
		background-color: rgb(83, 65, 163);
	}
	.tokenSelected {
		background-color: rgb(55, 187, 204);
		color: white;
	}
	.tokenInput {
		display: flex;
		width: 95%;
		border-radius: 10px;
		background-color: rgb(45, 44, 85);
		height: 100px;
		padding-right: 5px;
	}
	.tokenInput:focus {
		border: 2px solid rgb(55, 187, 204);
	}
	.amount {
		border: none;
		padding-left: 10px;
		width: 100%;
		border-radius: 25px;
		font-size: xx-large;
		background-color: rgb(45, 44, 85);
		color: white;
	}
	.amount:focus {
		outline: none;
	}
	.amount::-webkit-inner-spin-button {
		-webkit-appearance: none;
	}
</style>
