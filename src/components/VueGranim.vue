<template>
  <canvas :id="id" :name="name"></canvas>
</template>

<script>
  /* eslint-disable */
  import Granim from './granim/Granim'
  export default {
    name: 'vue-granim',
    props: {
      id: String,
      name: String,
      direction: {
        type: String,
        default: 'diagonal'
      },
      opacity: {
        type: Array,
        default: [1, 1]
      }
    },
    data () {
      return {}
    },
    computed: {
      canvasName () {
        return this.name
      }
    },
    mounted () {
      var VueGranim = new Granim({ // eslint-disable-line
        element: document.getElementById(this.id),
        name: 'granim',
        opacity: [1, 1],
        states: {
          'default-state': {
            gradients: [
              ['#834D9B', '#D04ED6'],
              ['#1CD8D2', '#93EDC7']
           ]
          }
        }
      })
    }
  }
</script>