<template>
  <form @submit.prevent="addTask">
    <input type="text" v-model="newTask.title" placeholder="Введите имя задачи">
    <textarea v-model="newTask.description" placeholder="Введите описание задачи"></textarea>
    <button type="submit">Добавить задачу</button>
  </form>
</template>

<script>
export default {
  name: 'TaskForm',
  data() {
    return {
      newTask: {
        title: '',
        description: ''
      }
    }
  },
  emits: 
    ['add-task'],
  methods: {
    addTask() {
      this.$emit('add-task', this.newTask);
      this.newTask = { title: '', description: '' };
    }
  }
}
</script>