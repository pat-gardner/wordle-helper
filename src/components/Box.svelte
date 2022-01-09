<script lang="ts">
    import { createEventDispatcher } from 'svelte'

    export let locked = false

    const dispatch = createEventDispatcher()

    let value: string
    $: {
        if(value) {
            value = value.charAt(value.length - 1)
        }
        dispatch('input', value)
    }
</script>

<input class="letter-input" type="text" disabled={locked} bind:value>

<style>
    .letter-input {
        width: 4rem;
        height: 4rem;
        text-align: center;
        text-transform: uppercase;
        caret-color: transparent;
    }
</style>