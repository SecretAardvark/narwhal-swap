<script src>
	import { onMount } from 'svelte';
	import {
		defaultEvmStores,
		connected,
		provider,
		chainId,
		//ChainData,
		// signer,
		signerAddress
		// contracts
	} from 'svelte-ethers-store';
	//import { e } from 'vitest/dist/index-5aad25c1';

	let title = 'Narwal Swap';
	let account;
	/**
	 * @type {string | any[]}
	 */
	let address;
	let isConnected;
	let currentNetwork;

	let networks = [
		{ name: 'ethereum', chainID: 1, ticker: 'eth' },
		{ name: 'avalanche', chainID: 43114, ticker: 'avax' },
		{ name: 'arbitrum', chainID: 42161, ticker: 'arb' },
		{ name: 'polygon', chainID: 137, ticker: 'matic' },
		{ name: 'optimism', chainID: 10, ticker: 'op' },
		{ name: 'moonbeam', chainID: 1284, ticker: 'glmr' }
	];

	function getWallet() {
		defaultEvmStores.setProvider();
		provider.subscribe((v) => {
			account = v;
			address = $signerAddress;

			networks.forEach((network) => {
				if (network.chainID === $chainId) {
					currentNetwork = network.ticker;
				}
			});
			connected.subscribe((v) => {
				isConnected = v;
			});
			// console.log(account);
			// console.log(isConnected);
		});
	}
	onMount(() => getWallet());

	//TODO: refactor 'tokenMenu' popup into it's own component'
	//TODO: change pointer icon on hover over token menu toggles, 'to' button, settings
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
		<button id="networkDisplay">{$chainId ? currentNetwork : `Network`}</button>
		<button
			id="connectButton"
			on:click={() => {
				console.log(connected);
				!connected ? getWallet() : console.log('already connected');
			}}
			>{connected && typeof address == 'string'
				? `${address.slice(0, 6)}.. ${address.slice(-4)}` //  `${$signerAddress.slice(0, 6)}..${$signerAddress.slice(-4)}`
				: 'Address'}</button
		>
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
