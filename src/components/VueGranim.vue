<template>
  <canvas :id="id"></canvas>
</template>
<script>
  /* eslint-disable */
  import Vue from 'vue'
  import Granim from './granim/Granim'
  export default {
    props: {
      id: String,
      name: String,
      opacity: Array,
      states: Object,
      isPausedWhenNotInView: {
        type: Boolean,
        default: true
      },
      transitionSpeed: {
        type: Number,
        default: 5000
      },
      direction: {
        type: String,
        default: 'diagonal'
      }
    },
    data () {
      return {
        VueGranim: ''
      }
    },
    computed: {
      getOpacity () {
        let opacity = []
        let defaultStates =  this.states['default-state'].gradients[0]
        this.defaultStates.foreach(state => {
          opacity.push(.5)
        })
      }
    },
    beforeCreate () {
    },
    mounted () {
      let self = this
      self.VueGranim = new Granim({ // eslint-disable-line
        element: document.getElementById(self.id),
        name: 'granim',
        opacity: self.opacity,
        isPausedWhenNotInView: self.isPausedWhenNotInView,
        transitionSpeed: self.transitionSpeed,
        states: self.states
      })

      if (self.direction) {
        self.VueGranim.direction = self.direction
      }
    },
    methods: {
      setDirection () {
      }
    },
    watch: {
      direction (val, oldValue) {
        var self = this
        self.VueGranim.direction = val
      }
    }
  }
</script>