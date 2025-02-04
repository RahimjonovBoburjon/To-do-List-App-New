<template>
    <div
        class="flex items-center justify-between bg-gray-800 p-4 rounded-lg shadow-md hover:shadow-lg transition-all duration-300">
        <!-- Checkbox va Matn -->
        <div class="flex items-center gap-4">
            <input type="checkbox" :checked="todo.completed" @change="$emit('toggle-complete', todo.id)"
                class="h-6 w-6 accent-green-500 rounded cursor-pointer border-gray-500 border-2" />
            <p :class="{
                'line-through text-gray-500': todo.completed,
                'text-white': !todo.completed,
            }" class="text-lg font-medium">
                {{ todo.text }}
            </p>
        </div>

        <!-- Delete Tugmasi -->
        <button @click="$emit('delete-todo', todo.id)"
            class="w-8 h-8 flex items-center justify-center bg-red-500 hover:bg-red-600 text-white rounded-full transition-all duration-300">
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