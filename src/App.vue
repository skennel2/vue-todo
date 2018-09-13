<template>

  <div id="app">
    <h1>{{ msg }}</h1>
    <TestComponent></TestComponent>
  </div>

</template>

<script>
import TestComponent from './components/TestComponent.vue';

export default {
  name: 'app',
  components : {
    'TestComponent' : TestComponent
  },
  data () {
    return {
      msg: 'Hello World!!'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}
</style>
