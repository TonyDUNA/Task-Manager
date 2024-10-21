<template>
  <li class="task" :class="{ completed: task.completed }">
    <input type="checkbox" v-model="task.completed">
    <label for="task" :class="{ completed: task.completed }">
      <h4>{{ task.title }}</h4>
      <p>{{ task.description }}</p>
    </label>
    <button @click="$emit('delete-task')">Удалить</button>  
    
    <!-- <button @click="showDetails = true">Подробнее</button>
    <div class="task-details" v-show="showDetails">
      <slot name="description"></slot>
      <button @click="showDetails = false">Закрыть</button>
    </div> -->


  </li>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: {
      type: Object,
      required: true
    }
  },
  // return {
  //     showDetails: false
  //   }
}
</script>

<style>
.task {
  background-color: yellow;
  border: 1px solid #ccc;
  padding: 10px;
  margin: 10px 0;
  list-style: none;
}
.task.completed {
  background-color: rgb(87, 215, 87);
  text-decoration: line-through;
}

</style>