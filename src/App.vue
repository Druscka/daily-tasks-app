<template>
  <div class="container">
    <Header title="Daily Tasks" />
    <Tasks 
    @toggle-reminder="toggleReminder"
    @delete-task="deleteTask" :tasks="tasks" />
  </div>
  
</template>

<script>

import Header from './components/Header'
import Tasks from './components/Tasks'

export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data () {
    return {
      tasks: [],
    }
  },
  methods: {
    deleteTask(id) {
      if(confirm('Are you sure you want to delete this task?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} :task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Car Service Appointment',
        day: '24th of February - 13:30',
        reminder: true,
      },
      {
        id: 2,
        text: 'Pick up Allan from Airport',
        day: '31st of March - 14:25',
        reminder: true,
      },
      {
        id: 3,
        text: 'Drinking session with the boys',
        day: '24th of June - 21:00',
        reminder: false,
      }
    ]
  }
}

</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');


* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Source Sans Pro', sans-serif;
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
