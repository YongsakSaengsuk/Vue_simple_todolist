<template >
    <div>
        <h1>{{ taskname }}</h1>
        <input type="checkbox">
        <button class="edit-btn" @click="emitEdit">Edit</button>
    </div>
</template>
<script>
export default {
    name: 'List',
    props: {
        taskID: Number,
        taskname: String,
        EditTask: Function
    }
    ,
    methods: {
        emitEdit() {
            this.$emit('editTask', { id: this.taskID, text: this.taskname })
        },
    
    }
}
</script>
<style lang="">
    
</style>