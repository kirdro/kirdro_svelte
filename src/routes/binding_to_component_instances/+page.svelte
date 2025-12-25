<script>
    import TodoList from './TodoList.svelte';
    import Back from "../../components/Back.svelte";

    const todos = $state([
        { id: 1, done: false, description: 'write some docs' },
        { id: 2, done: false, description: 'start writing blog post' },
        { id: 3, done: true, description: 'buy some milk' },
        { id: 4, done: false, description: 'mow the lawn' },
        { id: 5, done: false, description: 'feed the turtle' },
        { id: 6, done: false, description: 'fix some bugs' }
    ]);

    let uid = todos.length + 1;

    function remove(todo) {
        const index = todos.indexOf(todo);
        todos.splice(index, 1);
    }
</script>

<Back />
<div class="board">
    <input
            placeholder="what needs to be done?"
            onkeydown={(e) => {
			if (e.key !== 'Enter') return;

			todos.push({
				id: uid++,
				done: false,
				description: e.currentTarget.value
			});

			e.currentTarget.value = '';
		}}
    />

    <div class="todo">
        <h2>todo</h2>
        <TodoList todos={todos.filter((t) => !t.done)} {remove} />
    </div>

    <div class="done">
        <h2>done</h2>
        <TodoList todos={todos.filter((t) => t.done)} {remove} />
    </div>
</div>

<style>
    .board {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-column-gap: 2em;
        max-width: 42em;
        margin: 0 auto;
        padding: 1.5em;
    }

    .board > input {
        font-size: 1.1em;
        grid-column: 1/3;
        padding: 0.8em 1em;
        margin: 0 0 1.5rem 0;
        background: #3a3f4b;
        border: 1px solid #5a5f6b;
        border-radius: 4px;
        color: #fff;
    }

    .board > input::placeholder {
        color: #9ca3af;
    }

    .board > input:focus {
        outline: none;
        border-color: #6b7280;
    }

    h2 {
        font-size: 1.5em;
        font-weight: 300;
        color: #9ca3af;
        margin-bottom: 0.8em;
    }

    .todo, .done {
        min-height: 200px;
    }
</style>
