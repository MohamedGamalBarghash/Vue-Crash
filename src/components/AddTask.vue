<template>
    <form @submit="onSubmit">
        <label>Task</label>
        <input name="taskName" placeholder="Task name" type="text" v-model="text">
        <div style="height: 1em"></div>
        <label>Date/Time</label>
        <input name="Date" placeholder="Day" type="text" v-model="day">
        <div style="height: 1em"></div>
        <div style="justify-content: space-between;">
        <label>Reminder</label>
        <input name="reminder" type="checkbox" class="checkBox" v-model="reminder">
        </div>
        <div style="height: 2em"></div>
        <input :click='onSubmit' type="submit" value="Add" class="submitButton">
        <div style="height: 3em"></div>
    </form>
</template>

<script>
export default {
    name: "AddTask",
    data () {
        return {
            text: '',
            day: '',
            reminder: false,
        }
    },
    methods: {
        onSubmit (e) {
            e.preventDefault();

            if (!this.text) {
                alert("Please enter a task!");
                return;
            }

            const newData = {
                id: Math.floor(Math.random() * 10000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }
            this.$emit("add-task", newData);

            this.text = '';
            this.day = '';
            this.reminder = false;
        }
    },
    emits: ["add-task"],
}
</script>

<style scoped>
form {
    display: flex;
    flex-direction: column;
    font-family: monospace;
}

input {
    padding: 0.5em;
    box-sizing: border-box;
    margin: 2px 0px 10px 4px;
}

label {
    font-size: 1.5em;
    font-weight: bold;
    margin-bottom: 5px;
}

.checkBox {
    margin: 0px 0px 0px 500px;
    width: 1.5em;
    height: 1.5em;
}

.submitButton {
    background-color: black;
    color: white;
    margin: 0px;
    padding: 0px;
    height: 3em;
    border-radius: 7px;
}
</style>
