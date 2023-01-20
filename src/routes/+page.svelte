<script>
	// @ts-nocheck

	import './tokenDisplay.svelte';
	import TokenDisplay from './tokenDisplay.svelte';

	let tokenOne;
	let tokenTwo;

	let tokenOneAmount;
	let tokenTwoAmount;

	let settingsMenu = false;

	const switchToken = () => {
		let temp = tokenOne;
		tokenOne = tokenTwo;
		tokenTwo = temp;
	};

	const fakeSwap = () => {
		if (tokenOne == 'Select Token' || tokenTwo == 'Select Token') {
			alert('Select token first');
		} else if (tokenOneAmount <= 0 || tokenTwoAmount <= 0) {
			alert('Amounts must be greater than 0');
		} else {
			alert(`Swapped ${tokenOneAmount} ${tokenOne} for ${tokenTwoAmount} ${tokenTwo}`);
		}
	};
</script>

<div class="clr" />
<main>
	<!-- outer div -->
	<div id="swapCard">
		<!-- inner div -->
		<div id="swapTitle">
			<p id="swap">Swap</p>
			<img src="/settings.svg" id="settingsIcon" on:click={() => (settingsMenu = !settingsMenu)} />
		</div>

		<div id="swapContents">
			{#if settingsMenu}
				<div class="settingsMenu"><h2>Hey look at all these fancy settings...</h2></div>
			{/if}
			<TokenDisplay bind:currentToken={tokenOne} bind:amount={tokenOneAmount} id="amount1" />

			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<div on:click={() => switchToken()}>to:</div>

			<TokenDisplay bind:currentToken={tokenTwo} bind:amount={tokenTwoAmount} id="amount2" />

			<br />
			<button on:click={() => fakeSwap()}
				>{tokenOne === 'Select Token' || tokenTwo === 'Select Token'
					? 'Select a token'
					: 'Swap'}</button
			>
		</div>
	</div>
</main>

<style>
	.clr {
		clear: both;
	}
	.settingsMenu {
		background-color: antiquewhite;
		height: 300px;
		width: 90%;
		overflow-y: auto;
		list-style: none;
		position: absolute;
		top: 0px;
		left: 5%;
	}

	#swapCard {
		background-image: linear-gradient(
			to bottom right,
			rgba(207, 10, 207, 0.95),
			rgba(86, 3, 219, 0.863)
		);
		background-color: rgba(21, 13, 51, 0.932);

		font-size: large;
		margin: auto;
		width: 450px;
		display: flex;
		flex-direction: column;
		z-index: 7;
		border-radius: 20px;
	}

	#swapCard:hover {
		/* border: 2px solid rgb(55, 187, 204); */
	}
	#swapTitle {
		/* color: white; */
		display: flex;
		justify-content: center;
		align-items: center;
		width: 100%;
		margin: auto;
	}

	#swap {
		color: rgb(55, 187, 204);
		padding-left: 60px;
		font-family: 'scrypta';
		font-size: x-large;
		text-align: center;
		width: 100%;
		margin: auto;
	}
	#swapContents {
		display: flex;
		position: relative;
		flex-direction: column;
		justify-content: space-evenly;
		align-items: center;
		z-index: 8;
		/* width: 100%; */
	}
	#settingsIcon {
		float: right;
		margin-right: 10px;
		background-color: darkviolet;
	}
</style>
