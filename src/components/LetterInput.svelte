<script lang="ts">
    import Box from './Box.svelte'
    import Lock from './Lock.svelte'

    let locked = false
</script>

<div class="input-wrapper">
    <Box {locked} on:input />
    <Lock bind:locked />
</div>

<style>
    .input-wrapper {
        font-size: 2rem;
        display: flex;
        flex-direction: column;
    }
</style>