<script>
	import { onMount } from 'svelte';
	export let name;

	const APIKey = '3a05b33f-b8df-429f-8059-aa9e8b4a8195'
	const APIURL = 'http://localhost/tools/api.php'

	onMount(()=>{
		getLatest()
	})

	const getLatest = () => {
		let myHeaders = new Headers({accept: 'application/json'});
		// myHeaders.append('X-CMC_PRO_API_KEY', APIKey)
		let searchParams = new URLSearchParams()
		searchParams.set('start','1')
		searchParams.set('limit','2')
		searchParams.set('convert','USD')
		searchParams.set('CMC_PRO_API_KEY',APIKey)
		const myInit = {
			method: `GET`,
			headers: myHeaders,
		}
		fetch(APIURL+'?'+searchParams.toString(), myInit)
		.then(res => res.json())
		.then(result => {
				console.log("latest",result)
		})
		.catch(
			(error) => {alert(error.message)}
		)
	}


</script>

<style>
	h1 {
		color: purple;
	}
</style>

<div></div>