<template>
    <div class="todo_list">
        <div v-for="todo in todos" :key="todo.text">
            <v-checkbox v-if="todo.done === true" :input-value="todo.done" @change="toggle(todo)">
                <template v-slot:label>
                    <div>
                        {{ todo.text }}
                    </div>
                </template>
            </v-checkbox>
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