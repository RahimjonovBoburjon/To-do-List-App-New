<template>
    <div class="max-w-2xl mx-auto mt-10">
        <!-- Sarlavha -->
        <h1 class="text-4xl font-bold text-center mb-6 text-white">
            My To-Do List
        </h1>

        <!-- Input va tugma -->
        <div class="flex items-center gap-4 mb-6">
            <input v-model="newTodo" type="text" placeholder="Add a new task..."
                class="flex-grow p-3 rounded-lg border-2 border-gray-600 focus:outline-none focus:ring-2 focus:ring-blue-500" />
            <button @click="addTodo"
                class="bg-blue-500 hover:bg-blue-600 text-white px-6 py-3 rounded-lg transition-all duration-200">
                Add
            </button>
        </div>

        <!-- Vazifalar Ro'yxati -->
        <div class="space-y-4">
            <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" @toggle-complete="toggleComplete"
                @delete-todo="deleteTodo" />
        </div>
    </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
    components: { TodoItem },
    data() {
        return {
            todos: [
                { id: 1, text: "Learn Vue.js", completed: false },
                { id: 2, text: "Build a To-Do App", completed: true },
            ],
            newTodo: "",
        };
    },
    methods: {
        addTodo() {
            if (this.newTodo.trim() !== "") {
                this.todos.push({
                    id: Date.now(),
                    text: this.newTodo,
                    completed: false,
                });
                this.newTodo = "";
            }
        },
        toggleComplete(id) {
            const todo = this.todos.find((todo) => todo.id === id);
            if (todo) {
                todo.completed = !todo.completed;
            }
        },
        deleteTodo(id) {
            this.todos = this.todos.filter((todo) => todo.id !== id);
        },
    },
};
</script>