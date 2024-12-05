<template>
    <div>
        <form @submit.prevent="addnewText(inputvalue)">
            <input type="text" v-model="inputvalue">
            <button type="submit">Submit</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'Form',
    props: {
        addnewText: Function
    },
    data() {
        return {
            inputvalue: '',
        }

    },
    methods: {
        
    },
}
</script>
<style lang="">

</style>