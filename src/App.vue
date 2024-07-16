<template>
    <h1>CRYPTO</h1>
    <Input :changeAmount="changeAmount"/>
    <div className="selectors">
        <Selector :setCrypto="setCryptoFirst"/>
        <Selector :setCrypto="setCryptoSecond"/>
    </div>
</template>

<script>
import Input from './components/input'
import Selector from './components/selector'

export default {
    components: { Input, Selector },
    data() {
        return {
            amount: 0,
            cryptoFirst: '',
            cryptoSecond: ''
        }
    },
    methods: {
        changeAmount(val) {
            this.amount = val
        },
        setCryptoFirst(val) {
            this.cryptoFirst = val
        },
        setCryptoSecond(val) {
            this.cryptoSecond = val
        }
    }
}
</script>

<style>
.selectors {
    display: flex;
    justify-content: space-around;
    width: 700px;
    margin: 0 auto;
}
</style>
