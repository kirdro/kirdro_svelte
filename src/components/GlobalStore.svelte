<script lang="ts">

import {counter} from "../tools/shared.svelte.ts";
import PropsComponent from "./PropsComponent.svelte";



</script>


<div class="grid grid-cols-1 grid-rows-1 h-25 w-30 bg-amber-500 justify-items-center items-center">
    <button class="w-28 h-max bg-emerald-500 rounded-md" onclick={() => counter.count++}>
        Click: {counter.count}
    </button>
    <PropsComponent text={String(counter.count)}/>
</div>

{#if counter.count > 10}
    <button class="w-28 h-max bg-emerald-500 rounded-md" onclick={() => counter.count++}>
        Click: {counter.count}
    </button>
{/if}