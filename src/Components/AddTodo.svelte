<script>
  import Add from "carbon-icons-svelte/lib/Add.svelte";
  import { todoList } from "../stores/TodoStore.js";
  import { v4 as uuid } from "uuid";

  let todo = "";
  const handleAddTodo = () => {
    if (todo.length < 1) return;
    const addTodo = {
      id: uuid(),
      title: todo,
      completed: false,
    };
    todoList.update((todos) => [addTodo, ...todos]);
    todo = "";
  };
</script>

<form on:submit|preventDefault={handleAddTodo}>
  <div style="display : flex; width : 100%; gap : 10px; align-items : center">
    <input
      value={todo}
      on:input={(e) => (todo = e.currentTarget.value)}
      type="text"
      class="todo-input"
      style="flex : 1"
      placeholder="What do you want to do?"
    />
    <button class="btn">
      <Add size={24} />
    </button>
  </div>
</form>

<style>
  .todo-input {
    padding: 10px;
    background: none;
    border: 0px;
    border-bottom: 2px solid #ccc;
    outline: none;
    color: white;
    font-size: 2rem;
    font-weight: bold;
  }
  .btn {
    width: 48px;
    height: 48px;
    padding: 10px;
    background: #fe938c;
    border: none;
    border-radius: 100px;
    cursor: pointer;
  }

  .btn:hover {
    background: #fe7b72;
  }
</style>
