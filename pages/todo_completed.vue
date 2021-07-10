<template>
    <div>
        <div v-for="todo in todos" :key="todo.text">
            <span v-if="todo.done == true">
                {{ todo.text }}
            </span>
        </div>
    </div>
</template>
<script>
import { mapMutations } from 'vuex'

export default {
    data(){
      return{
        name: ''
      }
    },
    computed: {
      todos () {
        return this.$store.state.todos.list
      }
    },
    methods: {
      ...mapMutations({
        toggle: 'todos/toggle'
      }),
    }
}
</script>