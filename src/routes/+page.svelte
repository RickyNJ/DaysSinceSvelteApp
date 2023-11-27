<script>
	import PokemonShowcase from './pokemonShowcase.svelte';
	import { mons } from './raidDataPerMon';
	import { monsDict } from './raidDataPerMonDict';

	let chosenMons = [];
	let name = '6';
	function addPokemon(input) {
		if (input != '') {
			chosenMons = [...chosenMons, input];
			name = '';
		}
	}
</script>

<body>
	<h1 class="text-3xl font-bold underline">HI</h1>

	<div id="input-field">
		<input bind:value={name} />
		<button on:click={addPokemon(name)}>Check pokemon</button>
		<br /><br />
	</div>

	{#each chosenMons as mon}
		<PokemonShowcase pokemonID={mon} raidDate={monsDict[mon]} /><br />
	{/each}
</body>

<style>
    body {
        background-color: #28223f;
    }
</style>
