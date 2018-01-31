<template>
  <div>
    <b-field class="is-pulled-right">
      <b-radio-button v-model="visibility"
        native-value="all">
        <span>All ({{allCount}})</span>
      </b-radio-button>
      <b-radio-button v-model="visibility"
        native-value="active">
        <span>Active ({{activeCount}})</span>
      </b-radio-button>
      <b-radio-button v-model="visibility"
        native-value="completed">
        <span>Completed ({{completedCount}})</span>
      </b-radio-button>
    </b-field>
  </div>
</template>

<script>
import { store } from '@/store'
import { mapGetters } from 'vuex'
export default {
  computed: {
    ...mapGetters(['todos']),
    visibility: {
      get: function () {
        return store.state.visibility
      },
      set: function (newValue) {
        store.dispatch('changeVisibility', newValue)
      }
    },
    completedCount: function () {
      var result = 0
      for (var i = 0; i < this.todos.length; i++) {
        if (this.todos[i].completed) result++
      }
      return result
    },
    activeCount: function () {
      var result = 0
      for (var i = 0; i < this.todos.length; i++) {
        if (!this.todos[i].completed) result++
      }
      return result
    },
    allCount: function () {
      var result = 0
      for (var i = 0; i < this.todos.length; i++) {
        result++
      }
      return result
    }
  }
}
</script>
