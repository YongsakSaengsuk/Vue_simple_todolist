<template>
    <div class="list-container">
        <List v-for="task in taskstext" :key="task.id" :taskname="task.text" :taskID="task.id" />
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
        taskstext: Array
    }
}
</script>
<style lang="">

</style>