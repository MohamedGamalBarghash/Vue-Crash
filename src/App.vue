<template>
  <div style="padding: 10px;">
    <Header :showAddTask="showAddTask" @toggle-add-task="toggleAddTask" />
    <AddTask @add-task="addTask" v-show="showAddTask" />
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
    <p>dbl-click to mark the task as completed</p>
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data () {
    return {
      tasks: [],
      showAddTask: false,
    }
  },
  methods: {
    deleteTask (id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder (id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task);
    },
    addTask (task) {
      this.tasks = [...this.tasks, task];
    },
    toggleAddTask () {
      this.showAddTask = !this.showAddTask;
    }
  },
  created () {
    this.tasks = [{
      id: 1,
      text: "Meeting with doctor",
      day: "1st of October",
      reminder: true,
    },{
      id: 2,
      text: "Meeting with Mex",
      day: "2nd of October",
      reminder: false,
    },{
      id: 3,
      text: "Getting a life",
      day: "Never",
      reminder: false,
    }]
  }, 
}
</script>

<style scoped>
 div {
   border: 0.5px solid black;
 }

 p {
   padding-top: 2rem;
   text-align: center;
   font-size: 0.7rem;
   color: rgba(0,0,0, 0.5);
 }
</style>
