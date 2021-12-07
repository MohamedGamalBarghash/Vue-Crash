<template>
    <button :style="{background: color}" @click='$emit("toggle-add-task")'>{{text}}</button>
</template>

<script>
export default {
    name: "Button",
    props: {
        text: String,
        color: String,
    },
    emits: ["toggle-add-task"],
};
</script>

<style scoped>
button {
    background-color: green;
    padding: 1vw;
    margin: 1em 1em 1em 1em;
    color: white;
    font-weight: bold;
    font-family: monospace;
    border: 0px;
    border-radius: 0.5em;
}
</style>
