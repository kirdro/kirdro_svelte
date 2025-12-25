<script>
    import { Tween } from 'svelte/motion';
    import { cubicOut } from 'svelte/easing';
    import { browser } from '$app/environment';
    import Back from "../../components/Back.svelte";

    let progress = $state(browser
        ? new Tween(0, { duration: 400, easing: cubicOut })
        : { current: 0, target: 0 }
    );
</script>
<Back/>
<progress value={progress.current}></progress>

<button onclick={() => (progress.target = 0)}>
    0%
</button>

<button onclick={() => (progress.target = 0.25)}>
    25%
</button>

<button onclick={() => (progress.target = 0.5)}>
    50%
</button>

<button onclick={() => (progress.target = 0.75)}>
    75%
</button>

<button onclick={() => (progress.target = 1)}>
    100%
</button>

<style>
    progress {
        display: block;
        width: 100%;
    }
</style>
