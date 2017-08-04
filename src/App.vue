<template>
  <div id="app">
    <h1>direction: {{ direction }} </h1>
    <vue-granim id="my-id-canvas" :direction="direction" :opacity="opacity" :isPausedWhenNotInView="false" :states="states"></vue-granim>
    <div>
      <button @click="direction = 'radial'">radial</button>
      <button @click="direction = 'left-right'">left-right</button>
      <button @click="direction = 'diagonal'">diagonal</button>
    </div>

    <vue-granim id="test-2" :direction="direction2" :opacity="opacity" :states="states"></vue-granim>
    <div>
      <button @click="direction2 = 'radial'">radial</button>
      <button @click="direction2 = 'left-right'">left-right</button>
      <button @click="direction2 = 'diagonal'">diagonal</button>
    </div>
  </div>
</template>

<script>
import Hello from './components/Hello'
import VueGranim from './components/VueGranim'
export default {
  name: 'app',
  components: {
    Hello,
    VueGranim
  },
  data () {
    return {
      direction: 'top-bottom',
      direction2: 'radial',
      opacity: [0.4, 1],
      states: {
        'default-state': {
          gradients: [
            ['#fff', '#000'],
            ['#000', '#fff']
          ]
        }
      }
    }
  },
  created () {
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
