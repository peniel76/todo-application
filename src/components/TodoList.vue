<template>
    <div>
        <transition-group tag="ul" name="todo">
        <!-- <ul> -->
            <!-- <li v-for="(todoItem, index) in todoItems">
                <span>{{ todoItem }}</span>
                <button v-on:click="removeTodoItem(todoItem, index)">remove</button>
            </li> -->
            <li v-for="(todoItem, index) in todolist" v-bind:key="index">
                <span>{{ todoItem }}</span>
                <!-- 함수호출 시 변수 넘기는 방법 예시임 -->
                <button v-on:click="removeTodoItem(todoItem, index)">remove</button>
            </li>
        <!-- </ul> -->
        </transition-group>
    </div>
</template>

<script>
export default {
    props: ['todolist'],
    data() {
        return {
            todoItems: [],
        }
    },
    methods: {
        // fetchTodoItems: function() {
        //     for(var i=0; i<localStorage.length; i++) {
        //         var item = localStorage.key(i);
        //         this.todoItems.push(item);
        //     }
        // },
        removeTodoItem: function(todo, index) {
            console.log('deleted', todo, index);
            // localStorage.removeItem(todo);
            // arr.splice('시작할 배열 인덱스','갯수')
            // this.todoItems.splice(index,1); //화면에서만 안보이도록 함
            // localStorage.removeItem(todo);
            this.$emit('delete', todo, index);
        },
    },
    // created: function() {
    //     // 페이지가 생성되고 컴포넌트가 호출될 떄 실행되는 로직
    //     this.fetchTodoItems();
    // }
}
</script>

<style>
.todo-enter-active, .todo-leave-active {
  transition: all 1s;
}
.todo-enter, .todo-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>
