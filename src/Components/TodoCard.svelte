<script>
  import Card from "./Card.svelte";
  import TrashCan from "carbon-icons-svelte/lib/TrashCan.svelte";
  import { todoList } from "../stores/TodoStore.js";
  export let id = null;
  export let title = "";
  export let completed = false;
  const handleFinishTodo = () => {
    todoList.update((todos) => {
      const newTodo = todos.map((todo) => {
        if (todo.id === id) {
          return {
            ...todo,
            completed: !todo.completed,
          };
        }
        return todo;
      });
      return newTodo;
    });
  };

  const handleRemoveTodo = () => {
    todoList.update((todos) => {
      return todos.filter((todo) => todo.id !== id);
    });
  };
</script>

<Card
  on:click={handleFinishTodo}
  style="display : flex; justify-content : space-between; align-items : center; cursor : pointer"
>
  <h3 style="text-decoration : {completed ? 'line-through' : 'none'}">
    {title}
  </h3>
  <button on:click={handleRemoveTodo} class="btn">
    <TrashCan size={24} />
  </button>
</Card>

<style>
  .btn {
    background: none;
    border: none;
    cursor: pointer;
  }
</style>
