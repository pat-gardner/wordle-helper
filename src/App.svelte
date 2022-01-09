<script lang="ts">
	import LetterInput from './components/LetterInput.svelte'
</script>

<main>
	<p>
		This is a tool to help solve <a href="https://www.powerlanguage.co.uk/wordle/">Wordle</a> puzzles. 
		Lock in the letters you know and try to fill in the rest!
	</p>
	<div class="input-area-wrapper">
		<LetterInput on:input={({detail}) => console.log(detail)} />
		<LetterInput />
		<LetterInput />
		<LetterInput />
		<LetterInput />
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	.input-area-wrapper {
		margin: auto;
		display: flex;
		justify-content: center;
		gap: 0.3rem;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>