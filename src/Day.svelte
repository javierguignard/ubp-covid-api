<script>
	export let day;	
	function formatNumber(num) {
		try{
			return num.toString().replace(/(\d)(?=(\d{3})+(?!\d))/g, '$1,')
		}catch(e){
			return 'S/D'
		}
	}
	function formatDate(date){
		let ret = date.split('-')
		return `${ret[2]}/${ret[1]}/${ret[0]}`
	}	
</script>

<style>
	article {
		margin: 0 0 1em 0;
	}

	h1 {
		font-size: 1.4em;
		margin: 0;
		display: block;
	}
	td{
		text-align: center
	}
</style>

<tr>
		<td>{formatDate(day.Date.substring(0,10))}</td>
		<td>{formatNumber(day.Confirmed)}</td>		
		<td>{formatNumber(day.Deaths)}</td>
		<td>{formatNumber(day.Recovered)}</td>
		<td>{formatNumber(day.Active)}</td>		
</tr>