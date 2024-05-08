<template>
    <div class="space-y-2">
        <TodoItem v-for="todo in $store.state.todos" :key="todo.id" :todo="todo">
            <template #default>
    
            </template>
        </TodoItem>
        
    </div>
</template>

<script>

import TodoItem from '@/components/TodoItem';

export default {


    components: {
        TodoItem
    }
}

</script>