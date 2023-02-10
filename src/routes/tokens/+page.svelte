<script>
	import {
		defaultEvmStores,
		connected,
		provider,
		//chainId,
		// @ts-ignore
		//chainData
		// signer,
		signerAddress
		// contracts
	} from 'svelte-ethers-store';

	let balance = async () => {
		await $provider.getBalance($signerAddress, $provider.getBlockNumber());
	};
	$: currentBalance = balance();
</script>

<div>
	<div>
		{currentBalance}
	</div>
	<p>Display some info about ERC-20 tokens here.</p>
</div>
