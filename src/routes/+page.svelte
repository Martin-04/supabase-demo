<script>
	import { supabase } from '$lib/supabase';

	let promise = supabase.from('countries').select();
	let names = supabase.from('rabbits').select();

	let name = '';
	async function sendName() {
		const response = await fetch('/api/sendName', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify({ name })
		});
		const data = await response.text();
		console.log(data);
		name = '';
		names = supabase.from('rabbits').select();
	}
</script>

<div class="prose">
	<h1>API:</h1>

	<ul>
		<li>
			<a href="/api/hello?name=Martin">Link zur API mit Query-Parameter</a>
		</li>
		<li><a href="/api/hello/Martin">Link zur API mit Route-Paramter</a></li>
	</ul>
</div>

<form>
	<h2>All my Rabbits</h2>
	<input type="text" bind:value={name} /><br /><button class="btn" on:click={sendName}
		>Add Rabbit!</button
	>
</form>

<h2>Rabbit Name</h2>
{#await names}
	<span class="loading loading-bars loading-lg text-primary" />
{:then result}
	<ul>
		{#each result.data as rabbit (rabbit.id)}
			<li>{rabbit.name}</li>
		{/each}
	</ul>
{/await}


<!-- {#await promise}
	<div><span class="loading loading-dots loading-lg" /></div>
{:then result}
	<ul>
		{#each result.data as country}
			<li>{country.name}</li>
		{/each}
	</ul>
{/await} -->
