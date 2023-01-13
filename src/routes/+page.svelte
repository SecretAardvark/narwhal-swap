<script>
	import './tokenDisplay.svelte';
	import TokenDisplay from './tokenDisplay.svelte';

	let tokenOne;
	let tokenTwo;

	const switchToken = () => {
		let temp = tokenOne;
		tokenOne = tokenTwo;
		tokenTwo = temp;
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
			<TokenDisplay bind:currentToken={tokenOne} />

			<div on:click={() => switchToken()}>to:</div>

			<TokenDisplay bind:currentToken={tokenTwo} />

			<br />
			<button on:click={() => alert(`swapped ${tokenOne} for ${tokenTwo}`)} id="swapButton"
				>swap</button
			>
		</div>
	</div>
</main>

<style>
	.clr {
		clear: both;
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
		border: 2px solid rgb(55, 187, 204);
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
		/* float: right; */
		background-color: darkviolet;
	}
</style>
