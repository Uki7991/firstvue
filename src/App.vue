<template>
  <div>
    <keep-alive>
    <component :is="component"></component>
    </keep-alive>
    <button v-on:click="component = 'form-one'">Show form one</button>
    <button v-on:click="component = 'form-two'">Show form two</button>
  </div>
</template>

<script>
import formOne from './components/formOne'
import formTwo from './components/formTwo'

export default {
  name: 'App',
  components: {
    'form-one': formOne,
    'form-two': formTwo
  },
  data() {
    return {
      component: 'form-one'
    }
  },
  methods: {
  }
}
</script>

<style>
</style>
