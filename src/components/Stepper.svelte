<script lang="ts">
    let {increment, decrement} = $props()

    const _increment = () => increment()
    const _decrement = () => decrement()
</script>

<button onclick={_decrement}>-1</button>
<button onclick={_increment}>+1</button>
