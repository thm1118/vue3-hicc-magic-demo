<script setup>
import { RouterLink } from 'vue-router';
</script>
<template>
  <header class="header">
    <RouterLink to="/"><h1>待办事项</h1></RouterLink>
    <input
            type="text"
            class="new-todo"
            autofocus
            autocomplete="off"
            placeholder="输入待办事项?"
            @keyup.enter="
                // @ts-ignore
                $emit('add-todo', $event.target.value);
                // @ts-ignore
                $event.target.value = '';
            "
      />
  </header>
</template>