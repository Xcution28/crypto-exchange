<template>
    <div class="container">
        <input min="0" type="number" @input="changeAmount($event.target.value)" placeholder="Enter amount">
        <div class="inner">
            <button @click="convert()">Convert</button>
            <button @click="favourite()">Favourites</button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        changeAmount: {
            type: Function,
            required: true
        },
        convert: {
            type: Function,
            required: true
        },
        favourite: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.inner {
    display: flex;
    justify-content: center;
    column-gap: 32px;
}

input {
    margin-bottom: 32px;
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

button {
    padding: 16px 24px;
    color: #fff;
    text-transform: uppercase;
    cursor: pointer;
    background: #1a032d;
    border: 0;
    border-radius: 4px;
}
</style>
