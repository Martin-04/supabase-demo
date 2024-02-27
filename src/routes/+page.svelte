<script>
    import {supabase} from "$lib/supabase";
    
    let promise = supabase.from("countries").select();
</script>
<div class="prose">
<h1>Aufgaben:</h1>

<ul>
    <li>anstatt eines JS-Objekts das auf der Seite dargestellt wird, möchte ich ein Liste aller Länder</li>
    <li>
        integriere einen loading Spinner von DaisyUI in dein Projekt
    </li>
    <li> gibt die Vercel URL zu deinem Projekt via Aufgab in Teams ab.</li>

</ul>
</div>
<div>{JSON.stringify(promise)}</div>

{#await promise}
<div>...loading</div>
{:then result}
<div>{JSON.stringify(result)}</div>
{/await}
