

<template>

  <AddTask @add-task="addTask" />

  <Head title="Task Tracker" />
  <Button color="red" value="Add Task" />

  <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />

</template>

<script>
import Head from "./components/Head.vue"
import Button from "./components/Button.vue"
import Tasks from "./components/Tasks.vue"
import AddTask from "./components/AddTask.vue"

export default {
  name: 'App',
  components: {
    Head,
    Button,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    toggleReminder(id) {

      this.tasks.map((task) => {
        task.id === id ? { ...task, reminder: !task.reminder } :
          task
      })
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask]
    }
  },
  //lifecycle method to create the asset on load
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Meeting at Work',
        day: 'Sunday',
        reminder: true
      },
      {
        id: 2,
        text: 'Meeting In Chicago',
        day: 'Sunday',
        reminder: true
      },
      {
        id: 3,
        text: 'Meeting in New York',
        day: 'Sunday',
        reminder: true
      }
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
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