<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" class="holder" :class='[task.reminder ? "remained" : ""]'>
        <div class="joke">
            <h3>{{ task.text }}</h3>
            <h4>{{ task.day }}</h4>
        </div>
        <div class="opera">
            <img @click="onDelete(task.id)" src="red-x.png" title="Tap to delete the task">
        </div>
    </div>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object
    },
    methods: {
        onDelete(id) {
            this.$emit("delete-task", id);
        }
    },
    emits: ["delete-task", "toggle-reminder"]
}
</script>

<style scoped>
    .holder {
        text-align: left;
        background-color: rgb(230, 230, 230);
        margin: 0.4em 0em 0em 0em;
        padding: 1em;
        width: auto;
    }

    .remained {
        border-left: 5px solid green;
    }

    .joke {
        display: inline-block;
        width: 98%;
    }

    .opera {
        display: flex;
        height: 100%;
        justify-items: center;
        justify-content: center;
        align-items: center;
    }

    div {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    h3 {
        display: inline-block;
        width: 80%;
        margin: 0.2em;
        font-weight: bold;
    }

    h4 {
        display: inline-block;
        width: 80%;
        margin: 0.2em;
        font-weight: normal;
        font-size: 0.8em;
    }

    img {
        height: 25px;
        width: 25px;
    }

    img:hover {
        cursor: pointer;
    }
</style>