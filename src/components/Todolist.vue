<template>
  <div>
      <ul>
        <Todotask v-for="task in tasks" :key="task" :task='task'
        v-on:remove-todo="remove"> </Todotask>
      </ul>
  </div>
</template>

<script>
import Todotask from '@/components/Todotask'
export default {
  components: {
    Todotask,
  },
  props: ['tasks'],
  methods: {
    remove(id) {
      this.$emit('remove-todo', id)
    }
  }

}
</script>

<style>
  ul{
    list-style: none;
    margin: 0px;
    padding: 0px;
  }
</style>