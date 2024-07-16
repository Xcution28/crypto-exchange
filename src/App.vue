<template>
    <h1>CRYPTO</h1>
    <Input />
    <div className="selectors">
        <Selector />
        <Selector />
    </div>
</template>

<script>
import Input from './components/input'
import Selector from './components/selector'

export default {
    components: { Input, Selector }
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