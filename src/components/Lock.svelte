<script lang="ts">
    export let locked = false

    const setLockState = (state: boolean) => locked = state 
</script>

{#if locked}
    <i class="fas fa-lock" on:click={() => setLockState(false)}></i>
{:else}
    <i class="fas fa-lock-open" on:click={() => setLockState(true)}></i>
{/if}