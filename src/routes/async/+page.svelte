<script>

    import {roll} from "../../tools/roll.ts";
    import Back from "../../components/Back.svelte";

    let promise = $state(roll());
</script>

<Back/>

<button onclick={() => promise = roll()}>
    roll the dice
</button>
{#await promise}
    <p>...rolling</p>
{:then number}
    <p> you rolled a {number}</p>
{:catch error}
    <p>{error.message}</p>
{/await}
