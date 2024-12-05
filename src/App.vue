<script>
import Form from './components/Form.vue'

    export default {
      name: 'App',
      data() {
        return {
          tasks: [
            { id: 1, text: "Task 1" },
            { id: 2, text: "Task 2" },
            { id: 3, text: "Task 3" }
          ]
        }
      },
      components: {
        Form
      },
      methods: {
        saveText(value) {
          console.log(value)
          this.tasks.push({ id: this.tasks.length + 1, text: value })
        }
      }
    }
</script>

<template>
  <div>
    <h1>TODO LIST</h1>
    <Form :saveText="saveText"/>
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
