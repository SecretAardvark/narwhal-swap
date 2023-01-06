<script>
	import { each } from 'svelte/internal';
	import './tokenDisplay.svelte';
	import TokenDisplay from './tokenDisplay.svelte';

	let tokenOne;
	let tokenTwo;

	const switchToken = () => {
		let tokenOneVal = tokenOne;
		let tokenTwoVal = tokenTwo;

		tokenOne = tokenTwoVal;
		tokenTwo = tokenOneVal;
	};
</script>

<div class="clr" />
<main>
	<!-- outer div -->
	<div id="swapCard">
		<!-- inner div -->
		<div id="swapTitle">
			<p id="swap">Swap</p>
			<p id="settingsIcon">{'<settings icon>'}</p>
		</div>
		<div id="swapContents">
			<TokenDisplay bind:token={tokenOne} id="displayOne" />
			<div on:click={() => switchToken()}>to:</div>
			<TokenDisplay bind:token={tokenTwo} id="displayTwo" />

			<br />
			<button id="swapButton" on:click={() => alert(`swapped ${tokenOne} for ${tokenTwo}`)}
				>swap</button
			>
		</div>
	</div>
</main>

<style>
	/* main {
		display: flex;
		align-items: center;
		justify-content: center;
	}
	#swapCard {
		margin: auto;
		width: 450px;
		border: 3px solid black;
	}
	.token {
		border: 3px solid black;
		width: 85%;
		/* justify-content: center; 
		margin: auto;
	}
	#swapTitle {
		display: flex;
		justify-content: end;
		width: 100%;
		margin: auto;
	}
	#swap {
		text-align: left;
	}
	#settingsIcon {
		float: right;
	} */
</style>
