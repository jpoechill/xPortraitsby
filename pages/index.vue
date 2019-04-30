<template>
  <div>
    <!-- <transition name="fade" appear> -->
      <div class="container">
        <!-- <div class="row">
          <div class="col-md-12">
            <button @click="loadNext">Load next</button>
          </div>
        </div> -->
        <div class="row pt-1">
          <div v-for="(portrait, index) in portraits" :key="portrait.name" class="col-md-4 mb-2 pb-4">
              <nuxt-link :to="portrait.url">
                <transition name="fade" appear>
                  <img @load="onLoadHandler(index)" v-show="index < readyIndex" :src="portrait.thumbnail" class="w-100" alt="Portrait Tumbnail">
                </transition>
              </nuxt-link>
          </div>
        </div>
        <div class="row">
          <div class="col-md-12 mb-3 text-right">
            <h4>© 2019</h4>
          </div>
        </div>
      </div>
    <!-- </transition> -->
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data: function () {
    return {
      allLoaded: false,
      indexHasBeenLoaded: 0,
      readyIndex: 0,
      loaded: [],
      ttlLoaded: 0,
      waitingToLoad: [],
      readyToLoad: []
    }
  },
  computed: mapState([
    'portraits'
  ]),
  mounted () {
    let self = this

    let curr = 0

    this.portraits.forEach(function () {
      curr += 500
      setTimeout(function () {
        self.loadNext()
      }, curr)
    })
  },
  methods: {
    onLoadHandler (index) {
      // this.readyToLoad.push(index)

      // while (this.readyToLoad.includes(this.readyIndex)) {
      //   this.readyToLoad.splice(this.readyToLoad.indexOf(this.readyIndex), 1)
      //   this.readyIndex++
      // }

      console.log(index + ' : ' + this.readyIndex)
    },
    loadNext () {
      this.readyIndex++
    }
  },
  transition: {
    appear: true,
    name: 'fade'
  }
}
</script>

<style>
.panel {
  min-height: 360px;
}

.font-custom {
  color: #FFF;
  font-weight: 600;
  font-size: 200px;
  font-family: 'Helvetica Neue';
}

.bg-custom {
  background: linear-gradient(312deg, #ffffff, #EEE);
  background-size: 400% 400%;

  -webkit-animation: AnimationName 3s ease infinite;
  -moz-animation: AnimationName 3s ease infinite;
  animation: AnimationName 3s ease infinite;
}

@-webkit-keyframes AnimationName {
    0%{background-position:0% 50%}
    50%{background-position:100% 51%}
    100%{background-position:0% 50%}
}
@-moz-keyframes AnimationName {
    0%{background-position:0% 50%}
    50%{background-position:100% 51%}
    100%{background-position:0% 50%}
}
@keyframes AnimationName { 
    0%{background-position:0% 50%}
    50%{background-position:100% 51%}
    100%{background-position:0% 50%}
}
</style>
