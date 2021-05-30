<script>

	import { onMount } from 'svelte';
	import axios from 'axios';

	let backendUrl = "http://localhost:1337";

	let restaurants = [];
	let cars = [];
	

	
	onMount(async () => {

		axios.get(`${backendUrl}/restaurants`).then(res => {
			restaurants = res.data;
			console.log(restaurants);
		});

		axios.get(`${backendUrl}/cars`).then(res => {
			cars = res.data;
			console.log(cars);
		});


	});

</script>



<div class="container">
	{#each restaurants as resto}
	<div class="resto">
		<div class="resto-name">{resto.name}</div>
		<div class="resto-descr">{resto.description}</div>
		<div class="resto-bezirk">{resto.bezirk}</div>
		<img class="resto-img" src='{backendUrl + resto.picture[0].url}' alt="">
	</div>
{/each}
</div>


<div class="container">
	{#each cars as car}
	<div class="resto">
		<div class="car-name">{car.brand}</div>
		<div class="car-color">{car.color}</div>
		<div class="car-price">Price: {car.price}</div>
		<div class="car-price">Mileage: {car.mileage}</div>
	</div>
{/each}
</div>



<style>

	.container {
		width: 60%;
		margin: 0 auto;
		display: flex;
		margin-top: 3em;
	}

	.resto {
		flex: 1;
	}

	.resto-img {
		width: 250px;
		height: auto;
		border-radius: 5px;
	}
	
</style>