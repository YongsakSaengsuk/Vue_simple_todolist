<template>
    <div class="list-container">
        <List v-for="task in taskstext" :key="task.id" :taskname="task.text" :taskID="task.id" @editTask="emitEditTask" />
    </div>
</template>
<script>
import List from './List.vue'
export default {
    name: 'ListControl',
    components: {
        List
    },
    props: {
        taskstext: Array,
        EditTask: Function,
    },
    methods: {
        emitEditTask(task) {
            // Emit the event to parent
            console.log(task)
            this.$emit("edit-task", task);
        },
    }
}
</script>
<style lang="">

</style>