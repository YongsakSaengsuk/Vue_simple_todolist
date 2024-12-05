<template >
    <div>
        <h1>{{ taskname }}</h1>
        <input type="checkbox">
        <button class="edit-btn">Edit</button>
    </div>
</template>
<script>
export default {
    name: 'List',
    props: {
        taskID: Number,
        taskname: String,
    }
}
</script>
<style lang="">
    
</style>