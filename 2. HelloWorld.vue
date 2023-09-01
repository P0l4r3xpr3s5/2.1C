<template>
  <div class="todo-app">
    <div class="header">
      <h1>Todo App</h1>
    </div>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Enter a new task">
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <input type="checkbox" v-model="task.completed">
        <span :class="{ completed: task.completed }">{{ task.text }}</span>
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({
          text: this.newTask,
          completed: false
        });
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.header {
  background-color: rgb(68, 68, 68);
  padding: 10px;
  text-align: center;
  position: fixed;
  width: 25%;
  top: 0;
}

.header h1 {
  color: white;
  margin: 0;
}
.todo-app {
  max-width: 400px;
  margin: 50px auto 0 auto;
  text-align: center;
  font-family: Arial, sans-serif;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  margin: 10px 0;
}

.completed {
  text-decoration: line-through;
  color: #888;
}

button {
  margin-left: 10px;
  padding: 5px 10px;
  background-color: #f44336;
  border: none;
  color: white;
  cursor: pointer;
}

</style>
