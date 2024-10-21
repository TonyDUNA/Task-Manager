<template>
  <div id="app">
     <h1>Список задач</h1>
     <task-list @add-task="addTask" :tasks="tasks"></task-list>
  </div>
   
  
</template>

<script>
import TaskList from './components/TaskList.vue';

export default {
  name: 'App',
  components: {
    TaskList    
  },
  data() {
    return {
      tasks:   
 [
        { id: 1, title: 'Задача 1', description: 'Понять Vue.js слоты - не очень понятны', completed: false },
        { id: 2, title: 'Задача 2', description: 'Понять Vue.js основные принципы', completed: true },
        { id: 3, title: 'Задача 3', description: 'Понять Vue.js последовательность', completed: true   
}
        
      ]
    }
  },
  methods: {
    addTask(newTask) {
      this.tasks.push(newTask);
    }
  }
}
</script>

<style>

.task {
  padding: 10px;
  border: 1px solid #fff;
  margin-bottom: 10px;
}

</style>