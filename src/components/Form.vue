<template>
    <div>
        <form @submit.prevent="handletext">
            <input type="text" v-model="inputvalue">
            <button type="submit">Submit</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'Form',
    props: {
        saveText: Function
    },
    data() {
        return {
            inputvalue: '',
        }

    },
    methods: {
        handletext() {
            if (this.inputvalue)
                this.saveText(this.inputvalue);
            else
                alert("please Enter text");
        }
    },
}
</script>
<style lang="">

</style>