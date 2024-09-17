<svelte:options immutable={true} />

<script>
  import ToDoList from "./lib/ToDoList.svelte";
  import { v4 as uuid } from "uuid";

  let toDos = [
    {
      id: uuid(),
      title: "todo11",
      completed: false,
    },
    {
      id: uuid(),
      title: "todo12",
      completed: true,
    },
    {
      id: uuid(),
      title: "todo13",
      completed: false,
    },
    {
      id: uuid(),
      title: "todo14",
      completed: false,
    },
  ];

  const handleAddToDo = (event) => {
    event.preventDefault();
    // console.log(event.detail.title,'event');
    toDos = [
      ...toDos,
      {
        id: uuid(),
        title: event.detail.title,
        completed: false,
      },
    ];
  };

  const handleRemoveTodo = (e) => {
    toDos = toDos.filter((todo) => todo.id != e.detail.id);
  };

  const handleToggleToDo = (event) => {
    toDos = toDos.map((todo) => {
      if(todo.id === event.detail.id){
        return {...todo,completed:event.detail.value}
      }
      return {...todo}
    })
  }
  
</script>

<div>
  <ToDoList
    {toDos}
    on:addToDo={handleAddToDo}
    on:removeToDo={handleRemoveTodo}
    on:toggleToDo={handleToggleToDo}
  />
</div>
