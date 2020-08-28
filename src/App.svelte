<svelte:head>
  <title>Tabla Covid Argentina</title>
  <link rel="stylesheet" type="text/css" href="//cdn.datatables.net/1.10.15/css/jquery.dataTables.css"> 
</svelte:head>


<script>
  import { onMount } from "svelte";
  import Day from "./Day.svelte";
  import Days from "./Days.svelte";

  let days;
  let day;

</script>


<style>

  main {  
    font-size: 15px;
    height:80%
  }
  h1 {
    font-size: 25px;
    text-align: center;
    color: red;
	}

</style>
<body>
  <h1>El covid en Argentina</h1>
<main>
		<Days {days} />
</main>
</body>