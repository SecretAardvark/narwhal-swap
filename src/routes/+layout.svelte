<script src>
	let title = 'Narwal Swap';

	//TODO: Style popup token menu
	//TODO: make outer tokenInput div border highlight when inner # input selected
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
	header {
		font-family: 'scrypta';
		color: rgb(53, 187, 204);
		font-size: large;
		display: flex;

		background-image: linear-gradient(
			to bottom right,
			rgba(207, 10, 207, 0.95),
			rgba(86, 3, 219, 0.863)
		);
		justify-content: space-between;
		align-items: center;
		padding: 10px;
		margin-bottom: 10px;
	}
	header a {
		display: flex;
		text-decoration: none;
		font-family: 'Roboto', sans-serif;
		margin-top: 10px;
		text-align: right;
		align-items: center;
		justify-content: space-between;
		color: rgb(53, 187, 204);
		margin-left: 5px;
		margin-right: 5px;
		padding-left: 5px;
	}
	.links {
		display: flex;
		align-items: center;
		justify-content: right;
	}
	#wallet-info {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	#searchBar {
		margin-top: 20px;
		margin-bottom: 20px;
		width: 30%;
	}
	#networkDisplay {
		margin-left: 5px;
	}
</style>
