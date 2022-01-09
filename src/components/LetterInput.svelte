<script lang="ts">
    import Box from './Box.svelte'
    import Lock from './Lock.svelte'

    export let focused: boolean
    export let locked: boolean
    export let advanceFocus: () => void
    export let onFocus: () => void

</script>

<div class="input-wrapper">
    <Box {focused} {locked} {advanceFocus} {onFocus} />
    <Lock bind:locked />
</div>

<style>
    .input-wrapper {
        font-size: 2rem;
        display: flex;
        flex-direction: column;
    }
</style>