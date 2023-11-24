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

	.input-field {
		font-family: Montserrat, sans-serif;

		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;

		min-height: 100vh;
		margin: 0;
	}
</style>
