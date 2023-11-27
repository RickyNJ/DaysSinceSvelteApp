<script>
	import { onMount } from 'svelte';
    import axios from 'axios';

	export let pokemonID;
	export let raidDate;

	let pokemonName;

	$: imgUrl =
		'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/' +
		pokemonID +
		'.png';
	$: url = 'https://pokeapi.co/api/v2/pokemon/' + pokemonID;

	onMount(async() => {
		try {
            const res = await axios.get(url);
            var pokemon = res.data;
			pokemonName = pokemon.name;
        } catch (e) {
            error = e;
        }
	});
</script>

<div class="card-container">
	<img class="relative object-center" src={imgUrl} alt="user" />
	<h2>{pokemonName}</h2>
	<p>
		{#if raidDate != undefined}
			the pokemon was last seen in raids on <br>{raidDate}
		{:else}
			this pokemon has never been in raids
		{/if}
	</p>
	<div class="buttons">
		<button class="primary"> Message </button>
		<button class="primary ghost"> Following </button>
	</div>
	<div class="skills">
		<h6>Skills</h6>
		<ul>
			<li>UI / UX</li>
			<li>Front End Development</li>
		</ul>
	</div>
</div>

<style>
	
	.card-container {
	background-color: #231E39;
	border-radius: 5px;
	box-shadow: 0px 10px 20px -10px rgba(0,0,0,0.75);
	color: #B3B8CD;
	padding-top: 30px;
	position: relative;
	width: 350px;
	max-width: 100%;
	text-align: center;
}

</style>
