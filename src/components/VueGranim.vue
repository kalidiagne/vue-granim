<template>
  <canvas :id="id" :class="canvasClassList"></canvas>
</template>
<script>
  /* eslint-disable */
  import Vue from 'vue'
  import Granim from './granim/Granim'
  export default {
    props: {
      id: String,
      name: String,
      classes: Array,
      bgimage: String,
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
        GraminObject: Object,
        canvasClassList: String
      }
    },
    computed: {
      backgroundUrl () {
        return `url(${this.bgimage})`
      }
    },
    mounted () {
      // Set background image if props is defined 
      if (this.bgimage) this.setBackground()

      this.GraminObject = new Granim({
        element: document.getElementById(this.id),
        name: 'granim',
        opacity: this.opacity,
        isPausedWhenNotInView: this.isPausedWhenNotInView,
        transitionSpeed: this.transitionSpeed,
        states: this.states
      })

      if (self.direction) {
        this.GraminObject.direction = self.direction
      }
    },
    methods: {
      setBackground () {
        Object.assign(document.getElementById(this.id).style, {
          'background-size': 'cover',
          'background-image': this.backgroundUrl
        })
      },
      setDirection () {
      }
    },
    watch: {
      direction (direction, oldValue) {
        this.GraminObject.direction = direction
      },
      opacity (opacity, oldValue) {
        this.GraminObject.opacity = opacity
      },
      bgimage (image, oldValue) {
        this.setBackground()
      }
    }
  }
</script>