<template>
  <Dummy />
</template>

<script>
import Vue from 'vue'
import Dummy from '~/components/Dummy'

export default {
  name: 'IndexPage',
  mounted () {
    try {
      const Component = this.instanciateComponent()

      // should throw "Cannot read properties of undefined (reading '_app')"
      console.log('Content from <Dummy /> :', Component.configApp)
    } catch (err) {
      console.error('[Error from dynamic component in pages/index.vue]', err)
    }
  },
  methods: {
    instanciateComponent () {
      const DummyComponent = Vue.extend(Dummy)

      return new DummyComponent()
    },
  }
}
</script>
