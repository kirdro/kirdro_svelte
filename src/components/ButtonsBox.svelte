<script>
    let count = $state(0);

    const increment = () => count += 1;
</script>

<style>
    button {
        width: max-content;
        height: 30px;
        background: #00c6fb;
        padding: 0 10px;
        border-radius: 5px;
    }

</style>

<div>
    <button onclick={increment}>Click</button>

    <span>{count}</span>
</div>