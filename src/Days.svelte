<script>	
    import { Datatable, rows } from 'svelte-simple-datatables'
	import { onMount } from "svelte";
	import Day from "./Day.svelte";

	const settings = {
		rowCount: true,
        search: false,
        sortable: true,
        pagination: true,
        rowPerPage: 30,
        columnFilter: false,
		blocks: {
            searchInput: true, 
            paginationButtons: true,
            paginationRowCount: true,
        }
    }
	let days;
	var last=0;
	onMount(async () => {
		await fetch(`https://api.covid19api.com/total/country/argentina`)
			.then(r => r.json())
			.then(data => {
				days = data.reverse();
			});
	})
</script>

<style>
	.loading {
		opacity: 0;
		animation: 0.4s 0.8s forwards fade-in;
	}

	@keyframes fade-in {
		from { opacity: 0; }
		to { opacity: 1; }
	}

	
 	section{width:85%;margin:30px auto;height:100%;}
    

</style>


<section>
{#if days}

<Datatable settings={settings} data={days}>
    <thead>
        <th data-key="id">Fecha</th>
		<th data-key="confirmed">Confirmados</th>		
        <th data-key="deaths">Muertes</th>
        <th data-key="recovered">Recuperados</th>
        <th data-key="actives">Activos</th>
    </thead>
    <tbody>
    {#each $rows as day, index }
       <Day {day}/>
	{/each}
    </tbody>
</Datatable>

{:else}
	<p class="loading">loading...</p>
{/if}
</section>