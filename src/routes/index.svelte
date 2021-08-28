<script lang="ts">
	import { operationStore, query } from '@urql/svelte';

	export const CONTINENTS_QUERY = `
		query continents {
			continents {
					code
					name
			}
		}
	`;

	const continents = operationStore(
		CONTINENTS_QUERY,
		{},
		{
			requestPolicy: 'cache-and-network',
			url: 'https://countries.trevorblades.com',
			fetchOptions: { mode: 'cors' }
		}
	);

	query(continents);
</script>

{console.log('continents:', continents)}

<pre>{JSON.stringify($continents, null, 2)}</pre>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
