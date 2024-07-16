<template>
    <ul>
        <li @click="setCrypto('BTS')">Bitcoin</li>
        <li @click="setCrypto('ETH')">ETH</li>
        <li @click="setCrypto('USDT')">USDT</li>
    </ul>
</template>

<script>
export default {
    methods: {
        setCrypto: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped>
ul {
    list-style: none;
    width: 200px;
    padding: 0;
    border-radius: 4px;
    border: 4px solid #000;
}

li {
    display: block;
    background: #1a032d;
    color: #fff;
    padding: 20px 0;
}

li:hover, li:active {
    background: #24043e;
    cursor: pointer;
}
</style>
