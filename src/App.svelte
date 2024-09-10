<script>
  import ToDoList from './lib/ToDoList.svelte'
  import {v4 as uuid} from 'uuid'

  const toDos = [
    {
      id:uuid(),
      title:'todo11',
      completed: false,
    },
    {
      id:uuid(),
      title:'todo12',
      completed: true,
    },
    {
      id:uuid(),
      title:'todo13',
      completed: false,
    },
    {
      id:uuid(),
      title:'todo14',
      completed: false,
    }
  ]
</script>

<div>
  <ToDoList todos={toDos}/>
</div>