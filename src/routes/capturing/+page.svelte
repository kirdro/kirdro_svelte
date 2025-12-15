<script>
    import Back from "../../components/Back.svelte";
    import Stepper from "../../components/Stepper.svelte";

    let value = $state(0);

    const increment = () => value += 1;
    const decrement = () => value -= 1;

</script>

<Back />
<div onkeydowncapture={(e) => alert(`<div> ${e.key}`)} role="presentation">
    <input onkeydowncapture={(e) => alert(`<input> ${e.key}`)} />
</div>
<p>The current value is {value}</p>
<Stepper
        {increment}
        {decrement}
/>