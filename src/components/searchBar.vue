<template>
    <div class = "container">
        <input type="text" v-model="input" @keyup.enter="logInput">
    </div>
</template>

<script>
    export default {
        data() {
            return ({
                input: ''
            });
        },
        methods: {
            logInput() {
                this.$emit('changeData',this.input);
            }
        }
    }
</script>

<style scoped>
input {
    text-align: center;
    margin: 20px;
    font-size: 30px;
}
</style>
