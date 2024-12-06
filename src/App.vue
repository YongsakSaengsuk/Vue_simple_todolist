<script>
import Form from './components/Form.vue'
import ListControl from './components/ListControl.vue'
export default {
  name: 'App',
  data() {
    return {
      tasks: [
        { id: 1, text: "Task 1" },
        { id: 2, text: "Task 2" },
        { id: 3, text: "Task 3" }
      ],
      editingTask: null,
    }
  },
  components: {
    Form,
    ListControl,
  },
  methods: {
    addnewText(value) {
      if (this.editingTask) {
        const task = this.tasks.find((task) => task.id === this.editingTask.id);
        if (task) task.text = value;
        this.editingTask = null;
      } else {
        this.tasks.push({
          id: this.tasks.length ? this.tasks[this.tasks.length - 1].id + 1 : 1,
          text: value,
        });
      }
    },
    EditTask({ id, text }) {
      const task = this.tasks.find((task) => task.id === id);
      if (task) task.text = text;
      this.editingTask = null;
    },
    setEditingTask(task) {
      console.log("setEditingTask", task)
      this.editingTask = task;
    },
  }
}
</script>

<template>
  <div>
    <h1>TODO LIST</h1>
    <Form :editingTask="editingTask" @addnewText="addnewText" @editTask="EditTask" />
    <ListControl :taskstext="tasks" @edit-task="setEditingTask" />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
