<template>
  <v-row justify="center" align="center">
    <v-col sm="8" md="4" lg="4">
      <v-card>
        <v-row no-gutters>
          <v-tabs>
            <v-tab href="#tab-1">Pending</v-tab>
            <v-tab-item class="pl-5" value="tab-1">
              <todo-pending/>
            </v-tab-item>
            <v-tab href="#tab-2">Completed</v-tab>
            <v-tab-item class="pl-5" value="tab-2">
              <todo-completed/>
            </v-tab-item>
          </v-tabs>
        </v-row>
        <v-row no-gutters class="pl-5">
          <v-col lg="8">
            <v-text-field v-model="name" label="Add an item here"></v-text-field>
          </v-col>
          <v-col lg="2">
            <v-btn
              @click="addTodo"
              rounded
              color="primary"
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
        if(this.name !== ''){
          this.$store.commit('todos/add', this.name)
          this.name = ''
        }
      }
    }
}
</script>