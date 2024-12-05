<template >
    <div>
        <h1>{{ taskname }}</h1>
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