<template>
    <ul>
        <li @click="setCrypto('BTC')" :class="cryptoCurrent === 'BTC' ? 'active' : ''">BTC</li>
        <li @click="setCrypto('ETH')" :class="cryptoCurrent === 'ETH' ? 'active' : ''">ETH</li>
        <li @click="setCrypto('USDT')" :class="cryptoCurrent === 'USDT' ? 'active' : ''">USDT</li>
    </ul>
</template>

<script>
export default {
    props: {
        setCrypto: {
            type: Function,
            required: true
        },
        cryptoCurrent: {
            type: String,
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

li:hover, li.active {
    background: #8c00ff;
    cursor: pointer;
}
</style>
