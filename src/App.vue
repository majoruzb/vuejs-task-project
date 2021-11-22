<template>
<div class="container">
  <Header title="Assalomu alaykum MAJOR GAMER"/>
  <AddTask  @add-task="addTask"/>
  <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
</div>
    
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      if (confirm('Do you want to delete?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? { ...task, reminder: !task.reminder } : task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Test was created",
        day: "november 21 march 1989 at 2:30pm",
        reminder: true
      },
      {
        id: 2,
        text: "Test2 was created",
        day: "november 21 march 1989 at 2:30pm",
        reminder: false
      },
      {
        id: 3,
        text: "Test3 was created",
        day: "november 21 march 1989 at 2:30pm",
        reminder: true
      },
      {
        id: 4,
        text: "Test4 was created",
        day: "november 21 march 1989 at 2:30pm",
        reminder: true
      }
    ]
  }
};
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,600;0,700;1,400;1,500&display=swap');
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
