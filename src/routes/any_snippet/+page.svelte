<script>
import {colors} from "./data.ts";
import FilteredList from "../../components/any_snippet/FilteredList.svelte";
import Back from "../../components/Back.svelte";

</script>
<Back/>
<FilteredList
        data={colors}
        field="name"
>
    {#snippet header()}
        <header>
            <span class="color"></span>
            <span class="name">name</span>
            <span class="hex">hex</span>
            <span class="rgb">rgb</span>
            <span class="hsl">hsl</span>
        </header>
    {/snippet}

    {#snippet row(d)}
        <div class="row">
            <span class="color" style="background-color: {d.hex}"></span>
            <span class="name">{d.name}</span>
            <span class="hex">{d.hex}</span>
            <span class="rgb">{d.rgb}</span>
            <span class="hsl">{d.hsl}</span>
        </div>
    {/snippet}
</FilteredList>



<style>
    header, .row {
        display: grid;
        align-items: center;
        grid-template-columns: 2em 4fr 3fr;
        gap: 1em;
        padding: 0.1em;
        background: var(--bg-1);
        border-radius: 0.2em;
    }

    header {
        font-weight: bold;
    }

    .row:hover {
        background: var(--bg-2);
    }

    .color {
        aspect-ratio: 1;
        height: 100%;
        border-radius: 0.1em;
    }

    .rgb, .hsl {
        display: none;
    }

    @media (min-width: 40rem) {
        header, .row {
            grid-template-columns: 2em 4fr 3fr 3fr;
        }

        .rgb {
            display: block;
        }
    }

    @media (min-width: 60rem) {
        header, .row {
            grid-template-columns: 2em 4fr 3fr 3fr 3fr;
        }

        .hsl {
            display: block;
        }
    }
</style>
