<template>
    <div>
        <input v-on:keyup.enter="addTodo" type="text" v-model="inputText">
        <button v-on:click="addTodo">Add</button>
    </div>
</template>

<script>
export default {
    methods: {
        addTodo: function(){
            var value = this.inputText;
            this.$emit('add', value);
            // localStorage.setItem(value, value);
            // 브라우저에서 제공하는 스토리지 기능 사용, 확인은 application>스토리지>로컬스토리지에서 확인 가능함
            this.clearInput();
        },
        clearInput: function() {
            this.inputText = '';
        }
    },
    data() {
        return {
            inputText: ''
        }
    },
}
</script>

<style>

</style>
