<template>
  <div class="main">
    <vue-flux
      :options="fluxOptions"
      :images="fluxImages"
      :transitions="fluxTransitions[5]"
      ref="slider">
    </vue-flux>

    <button @click="$refs.slider.showImage('next')">NEXT</button>
  </div>
</template>

<script>
import { VueFlux, Transitions } from 'vue-flux';
// import 'vue-flux/dist/vue-flux.css';
import axios from "axios";

export default {
  name: 'Snapbooth-Slider',
  props: {
  },

  components: {
      'vue-flux': VueFlux
  },

  data: () => ({
      fluxOptions: {
         autoplay: true
      },
      fluxImages: [],
      fluxTransitions0: {
            transitionTurn3d: Transitions.transitionTurn3d
      },
      fluxTransitions1: {
            transitionBlinds2D: Transitions.transitionBlinds2D
      },
      fluxTransitions2: {
            transitionBlinds3D: Transitions.transitionBlinds3D
      },
      fluxTransitions: [
        {
            transitionBlocks1: Transitions.transitionBlocks1
        },
        {
            transitionBlocks2: Transitions.transitionBlocks2
        },
        {
            transitionBook: Transitions.transitionBook
        },
        {
            transitionCamera: Transitions.transitionCamera
        },
        {
            transitionConcentric: Transitions.transitionConcentric
        },
        {
            transitionCube: Transitions.transitionCube
        },
        {
            transitionExplode: Transitions.transitionExplode
        },
        {
            transitionFade: Transitions.transitionFade
        },
        {
            transitionFall: Transitions.transitionFall
        },
        {
            transitionKenburn: Transitions.transitionKenburn
        },
        {
            transitionRound1: Transitions.transitionRound1
        },
        {
            transitionRound2: Transitions.transitionRound2
        },
        {
            transitionSlide: Transitions.transitionSlide
        },
        {
            transitionSwipe: Transitions.transitionSwipe
        },
        {
            transitionWarp: Transitions.transitionWarp
        },
        {
            transitionWaterfall: Transitions.transitionWaterfall
        },
        {
            transitionWave: Transitions.transitionWave
        },
        {
            transitionZip: Transitions.transitionZip
        },
      ],
  }),

  mounted() {
      axios({ method: "GET", "url": "https://jsonplaceholder.typicode.com/photos" }).then(result => {
          var i = 0;
          if (Array.isArray(result.data)) {
              result.data.forEach(element => {
                  i++;
                  if ( i < 10 ) {
                    this.fluxImages.push(element.thumbnailUrl);
                  }
                  
              });
          }
          
      }, error => {
          console.error(error);
      });
  },
  methods: { }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.main {
  height: 100vh;
}
</style>
