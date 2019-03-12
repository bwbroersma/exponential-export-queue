<svelte:head>
	<title>{url}</title>
</svelte:head>

<h1>{url}</h1>

{#each list as i}
	<a href="{url}-{i}">{url}-{i}</a><br>
{/each}

<script>
	export let url;
	let list = url.length < 10 ? [0,1,2,3,4,5,6,7,8,9] : []
</script>
<script context="module">
	function sleep(delay) {
		return new Promise(resolve => setTimeout(resolve, delay));
	}

	export async function preload({ params, query }) {
		console.log('start', params.url);
		await sleep(2000);
		console.log('end', params.url);
		return { url: params.url };
	}
</script>