<template>
    <div>
        <form @submit.prevent="submitForm">
            <input type="text" v-model="inputvalue">
            <button type="submit" >Submit</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'Form',
    props: {
        addnewText: Function,
        editingTask: Object,
    },
    data() {
        return {
            inputvalue: '',
        }
    },
    methods: {
        submitForm() {
            if (this.isEditing) {
                // Emit editTask event with the updated task
                console.log(this.editingTask)
                this.$emit("editTask", { id: this.editingTask.id, text: this.inputvalue });
            } else {
                // Emit addnewText event for adding a new task
                this.$emit("addnewText", this.inputvalue);
            }
            this.inputvalue = ""; // Clear input field
        }
    },
    computed: {
        isEditing() {
            return !!this.editingTask;
        },
    }, watch: {

        editingTask(newTask) {
            this.inputvalue = newTask ? newTask.text : "";
        },
    },
}
</script>
<style lang="">

</style>