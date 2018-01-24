<template>
  <div>
    <p class="is-pulled-left">{{count}} item left</p>
    <visibility-input/>
  </div>
</template>

<script>
import VisibilityInput from '@/components/VisibilityInput'
import { mapGetters } from 'vuex'
export default {
  components: {
    VisibilityInput
  },
  computed: {
    ...mapGetters(['todos']),
    count: function () {
      var result = 0
      for (var i = 0; i < this.todos.length; i++) {
        if (!this.todos[i].completed) result++
      }
      return result
    }
  }
}
</script>
