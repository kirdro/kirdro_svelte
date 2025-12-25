<script>
    import Keypad from './Keypad.svelte';
    import Back from "../../components/Back.svelte";

    let pin = $state('');

    let view = $derived(pin
        ? pin.replace(/\d(?!$)/g, '•')
        : 'enter your pin');

    function onsubmit() {
        alert(`submitted ${pin}`);
    }
</script>

<Back />
<h1 style="opacity: {pin ? 1 : 0.4}">
    {view}
</h1>

<Keypad bind:value={pin} {onsubmit} />
