<template>
  <div id="app">
    <div>
      <vue-granim 
        id="my-id-canvas"
        bgimage="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRAvCvKiaIy0XB5kVrGDrjcN_8OARfPKZ2rdTv708OUz-Qo2s85SQ"
        :direction="direction"
        :opacity="opacity"
        :isPausedWhenNotInView="false"
        :states="states"></vue-granim>
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
      classes: ['class-1', 'class-2'],
      states: {
        'default-state': {
          gradients: [
            ['#fff', '#000'],
            ['#000', '#fff']
          ],
          transitionSpeed: 2000,
          loop: true
        }
      }
    }
  },
  created () {
    console.log(this)
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
