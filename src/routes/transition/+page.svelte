<script>
    import { fade, fly } from "svelte/transition";
    import Back from "../../components/Back.svelte";
    let visible = $state(true);
    let visible2 = $state(true);
    let visible3 = $state(true);

</script>

<Back />
<label>
    <input type="checkbox" bind:checked={visible} />
    visible
</label>

{#if visible}
    <p transition:fade>
        Fades in and out
    </p>
{/if}

<label>
    <input type="checkbox" bind:checked={visible2} />
    visible
</label>

{#if visible2}
    <p transition:fly={{ y: 200, duration: 2000 }}>
        Fades in and out
    </p>
{/if}

<label>
    <input type="checkbox" bind:checked={visible3} />
    visible
</label>

{#if visible3}
    <p in:fly={{ y: 200, duration: 2000 }} out:fade>
        Fades in and out
    </p>
{/if}