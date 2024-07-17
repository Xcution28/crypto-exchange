<template>
    <h1>CRYPTO</h1>
    <Input :changeAmount="changeAmount" :convert="convert" :favourite="favourite"/>
    <p v-if="error !== ''">{{ error }}</p>
    <p v-if="result !== 0" class="result-text">{{ result }}</p>
    <Favourite :favs="favs" v-if="favs.length > 0" :getFromFavs="getFromFavs" />
    <div class="selectors">
        <Selector :setCrypto="setCryptoFirst" :cryptoCurrent="cryptoFirst" />
        <Selector :setCrypto="setCryptoSecond" :cryptoCurrent="cryptoSecond" />
    </div>
</template>

<script>
import Input from './components/input'
import Selector from './components/selector'
import Favourite from './components/favourite.vue'
import CryptoConvert from 'crypto-convert'

const convert = new CryptoConvert();

export default {
    components: { Input, Selector, Favourite },
    data() {
        return {
            amount: 0,
            cryptoFirst: '',
            cryptoSecond: '',
            error: '',
            result: '',
            favs: []
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
        },
        favourite() {
            this.favs.push({
                from: this.cryptoFirst,
                to: this.cryptoSecond
            })
        },
        getFromFavs(index) {
            this.cryptoFirst = this.favs[index].from
            this.cryptoSecond = this.favs[index].to
        },
        async convert() {
            if (this.amount <= 0) {
                this.error = 'Enter a number greater than zero';
                return;
            }  else if(this.cryptoFirst === '' || this.cryptoSecond === '') {
                this.error = 'Select currency';
                return;
            } else if(this.cryptoFirst === this.cryptoSecond) {
                this.error = 'Choose a different currency';
                return;
            }
            this.error = '';

            await convert.ready();

            if(this.cryptoFirst === 'BTC' && this.cryptoSecond === 'ETH')
                this.result = convert.BTC.ETH(this.amount);
            else if(this.cryptoFirst === 'BTC' && this.cryptoSecond === 'USDT')
                this.result = convert.BTC.USDT(this.amount);
            else if(this.cryptoFirst === 'ETH' && this.cryptoSecond === 'BTC')
                this.result = convert.ETH.BTC(this.amount);
            else if(this.cryptoFirst === 'ETH' && this.cryptoSecond === 'USDT')
                this.result = convert.ETH.USDT(this.amount);
            else if(this.cryptoFirst === 'USDT' && this.cryptoSecond === 'BTC')
                this.result = convert.USDT.BTC(this.amount);
            else if(this.cryptoFirst === 'USDT' && this.cryptoSecond === 'ETH')
                this.result = convert.USDT.ETH(this.amount);
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
