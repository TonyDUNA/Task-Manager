<template>  
  <p>Всего задач: {{ totalTasks }}</p>
  <!-- <p>Выполнено задач: {{ completedTasksCount }}</p> -->
  <p v-if="completedTasksCount > 0">Выполнено задач: {{ completedTasksCount }}</p>
    <p v-else>Нет выполненных задач</p>
  <ul>    
    <task v-for="(task, index) in tasks" :key="task.id" :task="task" @delete-task="deleteTask(index)"/>

    <!-- <template #description>      
      <p>{{ task.description }}</p>
    </template> -->
  </ul>
  <task-form @add-task="addTask" />
  
</template>

<script>
import Task from './Task.vue';
import TaskForm from './TaskForm.vue';

export default {
  name: 'TaskList',
  components: {
    Task, 
    TaskForm
  },
  props: {
    tasks: {
      type: Array,
      required: true
    } 
    
  },
  emits: 
    ['add-task'],
  computed: {
    totalTasks() {  
      return this.tasks.length;
    },
    completedTasksCount() {
    return this.tasks.filter(task => typeof task.completed === 'boolean' && task.completed).length;
    }
  },
  
  methods: {    
    addTask(newTask) {
      this.$emit('add-task', newTask);
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    }
    
  }
}
</script>