<script src>
	let title = 'Narwal Swap';
</script>

<link rel="stylesheet" href="src\routes\styles.css" />
<header>
	<span class="links">
		<h1>{title}</h1>
		<div id="icon" />
		<a href="/">Swap</a>
		<a href="/tokens">Tokens</a>
		<a href="/NFT">NFTs</a>
		<a href="/pool">Pool</a>
	</span>
	<input type="text" id="searchBar" />
	<span id="wallet-info">
		<button id="networkDisplay">Network</button>
		<button id="connectButton">Address</button>
	</span>
</header>

<main>
	<slot />
</main>

<style>
	/* a {
		color: white;
		margin-top: 30px;
		margin-left: 5 px;
		margin-right: 5px;
		padding-left: 5px;
	}
	header {
		display: flex;
		background-color: rgb(207, 10, 207);
		justify-content: space-between;
	}
	.links {
		display: flex;
		text-align: right;
		justify-content: space-between;
	}
	#wallet-info {
		justify-content: space-between;
	} */
</style>
