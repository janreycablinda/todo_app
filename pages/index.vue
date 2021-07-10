<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="4">
      <v-card elevation="2">
        <v-tabs>
          <v-tab href="#tab-1">Pending</v-tab>
          <v-tab href="#tab-2">Completed</v-tab>
          <v-tab-item value="tab-1">
            <todo-pending/>
          </v-tab-item>
          <v-tab-item value="tab-2">
            <todo-completed/>
          </v-tab-item>
        </v-tabs>
        <v-row no-gutters>
          <v-col lg="8">
            <v-text-field v-model="name" label="Add an item here"></v-text-field>
          </v-col>
          <v-col>
            <v-btn
              @click="addTodo"
              rounded
              color="primary"
              dark
              class="mt-2"
            >
              Add item
            </v-btn>
          </v-col>
        </v-row>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
import { mapMutations } from 'vuex'
import TodoPending from './todo_pending.vue'
import TodoCompleted from './todo_completed.vue'

export default {
    data(){
      return{
        name: ''
      }
    },
    components: {
      TodoPending,
      TodoCompleted
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
      addTodo () {
        this.$store.commit('todos/add', this.name)
        this.name = ''
      }
    }
}
</script>