<script>
import Form from './components/Form.vue'
import ListControl from './components/ListControl.vue'
export default {
  name: 'App',
  data() {
    return {
      tasks: JSON.parse(localStorage.getItem('tasks')) || [],
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
      console.log(tasks)
      
    },
    EditTask({ id, text }) {
      const task = this.tasks.find((task) => task.id === id);
      if (task) task.text = text;
      this.editingTask = null;
    },
    setEditingTask(task) {
      this.editingTask = task;
    },
    setLocalStorage() {
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    }
  },
  watch: {
    tasks: {
      handler(newTasks) {
        // Save updated tasks to localStorage
        localStorage.setItem('tasks', JSON.stringify(newTasks));
      },
      deep: true, // Watch nested changes within tasks
    },
  },
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
