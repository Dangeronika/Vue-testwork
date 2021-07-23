<template>
  <div>
      <ul>
        <Todotask v-for="todo in todos" :key="todo" :todo='todo'
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
  props: ['todos'],
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