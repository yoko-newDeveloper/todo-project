<template>
    <div>
        <h1>todoリスト</h1>
        <!-- @submit.preventを追加 -->
        <form @submit.prevent="addTodo()">
            <input v-model="todo">
        </form>
        <ul>
            <li v-for="( todo, index ) in todos" :key="index">
                {{ todo }}
                <button @click="removeTodo(index)">完了</button>
            </li>
        </ul>
        </div>
    </template>
<script>
export default {
    name: 'TodoList',
    data() {
        return {
        todo: '',
        todos: [],
        }
    },
    // methodsプロパティを追加
    methods: {
        addTodo(){
        this.todos.push(this.todo); //--1
        this.todo = ''; //--2
        },
        // todoを削除するメソッド
        removeTodo(index) {
            this.todos.splice(index, 1);
        }
    }
}
</script>