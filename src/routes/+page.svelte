<script>
	import { supabase } from '$lib/supabase';

	let promise = supabase.from('countries').select();
</script>

<div class="prose">
	<h1>Aufgaben:</h1>

	<ul>
		<li>
			anstatt eines JS-Objekts das auf der Seite dargestellt wird, möchte ich ein Liste aller Länder
		</li>
		<li>integriere einen loading Spinner von DaisyUI in dein Projekt</li>
		<li>gibt die Vercel URL zu deinem Projekt via Aufgab in Teams ab.</li>
	</ul>
</div>

{#await promise}
	<div><span class="loading loading-dots loading-lg" /></div>
{:then result}
	<ul>
		{#each result.data as country}
			<li>{country.name}</li>
		{/each}
	</ul>
{/await}
