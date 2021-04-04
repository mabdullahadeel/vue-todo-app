<template>
  <div class="main-container">
    <Header title="VueTracker" />
    <TaskContainer :tasks="tasks" :OpenAddTaskModal="openTaskModal" :updateTask="updateTask"/>
    <TaskModal v-if="showModal" :closeModal="hideModal" :mode="mode" :tasks="tasks" :currentID="currentID" />
  </div>
</template>

<script>
import Header from "./components/Header";
import TaskContainer from './components/TaskContainer';
import TaskModal from './components/TaskModal';

import Tasks from './assets/data/tasks';
export default {
  name: "App",
  components: {
    Header,
    TaskContainer,
    TaskModal,
  },
  data() {
    return {
      tasks: [],
      showModal: false,
      mode: "add",
      currentID: null,
    }
  },
  created(){
    this.tasks = Tasks
  },
  methods: {
    openTaskModal(){
      this.showModal = true
    },
    hideModal(){
      this.showModal = false
      this.mode = "add"
      this.currentID = null
    },
    updateTask(taskID){
      this.mode = "update";
      this.currentID = taskID;
      this.showModal = true
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}

.main-container{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
</style>