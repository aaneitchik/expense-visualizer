<script context="module" lang="ts">
	import type { Load } from '@sveltejs/kit';

	export const load: Load = async ({ fetch }) => {
		const response = await fetch('/api/sheet');

		if (response.ok) {
			const { sheet } = await response.json();
			return { props: { sheet } };
		}

		return {
			status: response.status,
			error: new Error('Could not load document')
		};
	};
</script>

<script>
	export let sheet;
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<p>Sheet loaded: {sheet}</p>
