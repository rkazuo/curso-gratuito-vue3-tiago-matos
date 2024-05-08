<template>
  <div class="px-3 py-10 md:px-10">
    <div class="w-full sm:w-1/2 lg:w-1/3 mx-auto">
      <TodoSpinner v-if="loading"/>

      <template v-else>
        <TodoFormAdd />
        <TodoItems v-if="$store.state.todos.length" />
        <TodoEmpty v-else/>
      </template>
    </div>
  </div>
  <!--/ Content -->


</template>

<script>
import { ref } from 'vue';
import { useStore } from 'vuex'
import TodoSpinner from '@/components/TodoSpinner';
import TodoFormAdd from '@/components/TodoFormAdd';
import TodoItems from '@/components/TodoItems';
import TodoEmpty from '@/components/TodoEmpty';

export default {
  name: 'App',
  components: {
    TodoSpinner, TodoFormAdd, TodoItems, TodoEmpty
  },

  setup() {
    const loading = ref(false);
    const store = useStore();

    loading.value = true
    store.dispatch('getTodos').finally( 
      () => loading.value = false
    );

    return {
      loading
    }
  },


  created() {
    
    
  }
}
</script>
