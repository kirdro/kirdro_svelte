<script>
    let array = $state([1,2,3,4])

    let total = $derived(array.length)

    const increment = () => {
        array.push(array[array.length - 1] + 1)
    }


    console.log('>>>>>>>>>>>1', $state.snapshot(array))
    $inspect(array)
</script>

<div>
    <button onclick={increment}>Click</button>
    <span>
        {JSON.stringify(array)}
        {total}
    </span>
</div>