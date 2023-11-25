<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <p class="display-3">Vue crash course</p>
            </div>
        </div>

        <div class="row">
            <dic class="col-12 col-lg-6">
                <NewTodo @on-addtodo="addTodo($event)" />
            </dic>
        </div>

        <br />

        <div class="row">
            <div class="col-12 col-lg-6">
                <ul class="list-group">
                    <TodoItem v-for="(todos, index) in todos" 
                        :key="index"
                        :todoString="todos.todoString"
                        :completed="todos.completed"
                        @on-delete="deleteTodo(todos)"
                        @on-toggle="toggleTodo(todos)"
                        @on-edit="editTodo(todos, $event)"
                    />
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
import NewTodo from "./NewTodo.vue"
export default {
    components: {
        TodoItem, NewTodo
    },

    data(){
        return{
            todos: [
                {todoString: "Spend some more time coding", completed: false},
                {todoString: "Cook some food", completed: true},
                {todoString: "Watch Crash courses", completed: true},
                {todoString: "watch tv", completed: false},
            ]
        }
    },

    methods: {
        addTodo(newTodo){
            this.todos.push({
                todoString: newTodo,
                completed: false
            })
        },
        toggleTodo(todo){
            todo.completed = !todo.completed;
        },
        editTodo(todo, newTodoString){
            todo.todoString = newTodoString;
        },
        deleteTodo(deleteTodo){
            this.todos = this.todos.filter(todo => todo.todoString !== deleteTodo.todoString);
        }
    }
}
</script>

<style>

</style>