<template>
    <div
        class="flex items-center justify-between bg-white rounded-lg p-4 shadow-md hover:shadow-lg transition-all duration-300">
        <!-- Checkbox va Vazifa Matni -->
        <div class="flex items-center gap-4">
            <input type="checkbox" :checked="todo.completed" @change="$emit('toggle-complete', todo.id)"
                class="h-5 w-5 accent-green-500 rounded cursor-pointer" />
            <p :class="{
                'line-through text-gray-400': todo.completed,
                'text-gray-800': !todo.completed,
            }" class="text-lg font-semibold">
                {{ todo.text }}
            </p>
        </div>

        <!-- O'chirish tugmasi -->
        <button @click="$emit('delete-todo', todo.id)"
            class="flex items-center justify-center w-8 h-8 bg-red-500 hover:bg-red-600 text-white rounded-full transition-all duration-200"
            aria-label="Delete Task">
            🗑️
        </button>
    </div>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true,
        },
    },
};
</script>

<style scoped></style>