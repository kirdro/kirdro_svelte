<script lang="ts">


    import Thing from "../../components/Thing.svelte";
    import Back from "../../components/Back.svelte";

    let things = $state([
        { id: 1, name: 'apple' },
        { id: 2, name: 'banana' },
        { id: 3, name: 'carrot' },
        { id: 4, name: 'doughnut' },
        { id: 5, name: 'egg' }
    ]);
</script>
<Back />
<button onclick={() => things.shift()}>
    Remove first thing
</button>

{#each things as thing (thing.id)}
    <Thing name={thing.name} />
{/each}
