<script lang="ts">
	import LetterInput from './components/LetterInput.svelte'

	const len = 5
	let lockStates = [false, false, false, false, false]
	let focusedIndex = 0

	/**
	 * Find the next unlocked letter input after the currently focused
	 * input and focus it. If the search reaches the last input, wrap
	 * around to the first. If no other inputs are unlocked, stay
	 * focused on the current one.
	 */
	const advanceFocus = () => {
		for (let i = focusedIndex + 1; i < focusedIndex + len; i++) {
			const currInput = lockStates[i % len]
			if (!currInput) {
				focusedIndex = i % len
				break
			}
		}
	}

	/**
	 * If focus is set some other way (eg clicking on a box), call
	 * this to set the focused index.
	 * @param index the index of the new focused element
	 */
	const setFocus = (index: number) => focusedIndex = index
</script>

<main>
	<p>
		This is a tool to help solve <a href="https://www.powerlanguage.co.uk/wordle/" target="_blank">Wordle</a> puzzles. 
		Lock in the letters you know and try to fill in the rest!
	</p>
	<div class="input-area-wrapper">
		{#each lockStates as locked, i}
			<LetterInput
				{advanceFocus}
				onFocus={() => setFocus(i)}
				bind:locked={locked}
				focused={i === focusedIndex}
			/>
		{/each}
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