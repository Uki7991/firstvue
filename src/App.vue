<template>
  <div>
    <form-helper>
      <div slot="form-header">
        <h3>This is title of the form</h3>
        <p>Information about the form</p>
      </div>
      <div slot="form-fields">
        <input type="text" placeholder="name" required>
        <input type="password" placeholder="password" required>
      </div>
      <div slot="form-controls">
        <button v-on:click="handleSubmit">Submit</button>
      </div>
    </form-helper>
  </div>
</template>

<script>
import FormHelper from './components/FormHelper'

export default {
  name: 'App',
  components: {
    'form-helper': FormHelper
  },
  data() {
    return {
      title: 'I am dynamic title'
    }
  },
  methods: {
  }
}
</script>

<style>
</style>
