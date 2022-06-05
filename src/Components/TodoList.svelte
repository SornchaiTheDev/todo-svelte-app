<script>
  import TodoCard from "./TodoCard.svelte";
  export let todos = []
</script>

<div class="todo-list">
  {#each todos as todo (todo.id)}
    <TodoCard title={todo.title} completed={todo.completed} id={todo.id} />
  {/each}
</div>

<style>
  .todo-list {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
</style>
