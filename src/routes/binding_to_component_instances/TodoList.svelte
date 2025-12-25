<script>
    import { flip } from 'svelte/animate';
    import { send, receive } from './transition.js';
    let { todos, remove } = $props();
</script>

<ul class="todos">
    {#each todos as todo (todo.id)}
        <li
                class={{ done: todo.done }}
                in:receive={{ key: todo.id }}
                out:send={{ key: todo.id }}
                animate:flip={{ duration: 200 }}
        >
            <label>
                <input type="checkbox" bind:checked={todo.done}/>
                <span>{todo.description}</span>
                <button onclick={() => remove(todo)} aria-label="Remove"></button>
            </label>
        </li>
    {/each}
</ul>

<style>
    .todos {
        list-style: none;
        padding: 0;
        margin: 0;
    }

    li {
        background: #3a3f4b;
        margin-bottom: 2px;
    }

    li:nth-child(even) {
        background: #32363f;
    }

    label {
        width: 100%;
        display: flex;
        align-items: center;
        padding: 0.7em 1em;
        cursor: pointer;
        gap: 0.8em;
    }

    input[type="checkbox"] {
        width: 18px;
        height: 18px;
        accent-color: #06b6d4;
        cursor: pointer;
        flex-shrink: 0;
    }

    span {
        flex: 1;
        color: #e5e7eb;
        font-size: 0.95em;
    }

    li.done span {
        color: #6b7280;
        text-decoration: line-through;
    }

    button {
        width: 20px;
        height: 20px;
        background: transparent;
        background-image: url(./remove.svg);
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
        border: none;
        cursor: pointer;
        opacity: 0.4;
        transition: opacity 0.2s;
        padding: 0;
    }

    button:hover {
        opacity: 0.8;
    }
</style>
