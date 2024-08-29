<script setup>
import { computed } from 'vue';
import { useRoute, RouterLink } from 'vue-router';

const props = defineProps(['todos']);
const route = useRoute();
const remaining = computed(() => props.todos.filter(todo => !todo.completed).length);
</script>

<template>
    <footer class="footer" v-show="todos.length > 0">
        <span class="todo-count">
            剩余 <strong> {{ remaining }}</strong> {{ remaining === 1 ? "个" : "个" }} 待办
        </span>
        <ul class="filters">
            <li><RouterLink to="/" :class="{ selected: route.name == 'all' }">所有</RouterLink></li>
            <li><RouterLink to="/active" :class="{ selected: route.name == 'active' }">处理中</RouterLink></li>
            <li><RouterLink to="/completed" :class="{ selected: route.name == 'completed' }">已完成</RouterLink></li>
        </ul>
        <button class="clear-completed" v-show="todos.some(todo => todo.completed)" @click="$emit('delete-completed')">清理已完成</button>
    </footer>
</template>