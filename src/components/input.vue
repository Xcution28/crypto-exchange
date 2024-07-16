<template>
    <input type="number" @input="changeAmount($event.target.value)" placeholder="Enter amount">
</template>

<script>
export default {
    props: {
        changeAmount: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped>
input {
    outline: none;
    width: 500px;
    position: relative;
    top: -50%;
    font-size: 1.25em;
    border-radius: 4px;
    border: 4px solid #1a032d;
    padding: 16px 24px;
    background: #fafafa;
    color: #333;
}
</style>
