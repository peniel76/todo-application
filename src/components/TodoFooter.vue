<template>
    <div>
        <button v-on:click="TodoClearAll">clear All</button>
    </div>
</template>

<script>
export default {
    methods: {
        TodoClearAll: function() {
            // localStorage.clear();
            this.$emit('remove');
        }
    }
}
</script>

<style>

</style>
