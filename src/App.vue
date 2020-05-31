<template>
  <div>
    <app-header :title="title" v-on:changeTitle="changeTitle($event)"></app-header>
    <ninjas :ninjas="ninjas"></ninjas>
    <app-footer :title="title"></app-footer>
  </div>
</template>

<script>
import NinjasVue from './components/Ninjas.vue'
import HeaderVue from './components/Header.vue'
import FooterVue from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    'ninjas': NinjasVue,
    'app-header': HeaderVue,
    'app-footer': FooterVue
  },
  data() {
    return {
      title: 'Hello, World',
      ninjas: [
                {name: 'Ryu', speciality: 'Vue Components', show: false},
                {name: 'Crystal', speciality: 'HTML Wizardry', show: false},
                {name: 'Hitoshi', speciality: 'Click Events', show: false},
                {name: 'Tango', speciality: 'Conditionals', show: false},
                {name: 'Kami', speciality: 'Webpack', show: false},
                {name: 'Yoshi', speciality: 'Data Diggin', show: false}
            ]
    }
  },
  methods: {
    changeTitle(updatedTitle) {
      this.title = updatedTitle
    }
  }
}
</script>

<style>
</style>
