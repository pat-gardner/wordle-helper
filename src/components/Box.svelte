<script lang="ts">
    import { afterUpdate } from 'svelte'

    export let focused: boolean
    export let locked: boolean
    export let advanceFocus: () => void
    export let onFocus: () => void

    let input: HTMLInputElement

    // Value will always be the most recent single character typed
    const onInput = (e: any) => {
        input.value = e.data || ''
        if (e.data) advanceFocus()
    }

    afterUpdate(() => {
        if (focused) {
            input.focus()
        }
    })
</script>

<input class="letter-input" type="text" disabled={locked} bind:this={input} on:focus={onFocus} on:input={onInput}>

<style>
    .letter-input {
        width: 4rem;
        height: 4rem;
        text-align: center;
        text-transform: uppercase;
        caret-color: transparent;
    }
</style>