<script>
  import AddTodo from "./Components/AddTodo.svelte";
  import TodoList from "./Components/TodoList.svelte";
  import { todoList } from "./stores/TodoStore.js";
  let showCompleted = false;
  $: todos = $todoList.filter((todo) => {
    if (!showCompleted) {
      return !todo.completed;
    }
    return true;
  });
</script>

<div class="container">
  <AddTodo />
  <div
    style="display : flex; justify-content : space-between; align-items : center"
  >
    <h2 class="heading-1">Todo ({todos.length})</h2>
    <div class="checkbox-group">
      <input
        type="checkbox"
        class="checkbox"
        on:change={(e) => (showCompleted = e.currentTarget.checked)}
      />
      <h3>Show Completed</h3>
    </div>
  </div>
  <TodoList {todos} />
</div>

<style>
  .heading-1 {
    color: white;
  }

  .container {
    padding-top: 5%;
    max-width: 728px;
    margin: 0 auto;
  }
  .checkbox-group {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    color: white;
  }
</style>
