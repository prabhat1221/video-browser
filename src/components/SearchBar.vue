<template>
    <div>
        <input @input="onInput"/>
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    data() {
        return {inputText:''}
    },
    methods: {
        onInput(event) {
            this.$emit('termChange', event.target.value);
        }
    }
}
</script>

<style scoped>
input{
    width: 75%;
}
div{
    text-align: center;
    margin: 1em;
}

</style>