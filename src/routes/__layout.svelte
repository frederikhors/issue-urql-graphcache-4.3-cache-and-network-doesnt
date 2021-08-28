<script lang="ts">
	import { initClient, dedupExchange, fetchExchange } from '@urql/svelte';
	import { offlineExchange } from '@urql/exchange-graphcache';
	import { makeDefaultStorage } from '@urql/exchange-graphcache/default-storage';

	const storage = makeDefaultStorage({
		idbName: 'myCache',
		maxAge: 7
	});

	const exchanges = [
		dedupExchange,
		offlineExchange({
			storage
		}),
		fetchExchange
	];

	function OnInit(): void {
		initClient({
			url: 'https://countries.trevorblades.com',
			exchanges
		});
	}

	OnInit();
</script>

<slot />
