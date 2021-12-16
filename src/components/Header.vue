<template>
    <header>
        <p>Task Manager</p>
        <Button title="Tap to show/unshow the Add Task form" @toggle-add-task="$emit('toggle-add-task')" :text='showAddTask ? "Close" : "Add Task"' :color='showAddTask ? "red" : "green"' />
    </header>
</template>

<script>
import Button from "./Button";

export default {
    name: "Header",
    components: {
        Button
    },
    props: {
        showAddTask: Boolean,
    },
    emits: ['toggle-add-task']
}
</script>