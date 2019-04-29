<template>
  <div>
    <transition name="fade" appear>
      <div class="container">
        <div class="row pt-1">
          <div v-for="(portrait, index) in portraits" :key="portrait.name" class="col-md-4 mb-2 pb-4">
              <nuxt-link :to="portrait.url">
                <transition name="fade" appear>
                  <img @load="onLoadHandler(index)" v-show="index <= indexHasBeenLoaded" :src="portrait.thumbnail" class="w-100" alt="Portrait Tumbnail">
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
    </transition>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data: function () {
    return {
      allLoaded: false,
      indexHasBeenLoaded: 0,
      loaded: [],
      ttlLoaded: 0
    }
  },
  computed: mapState([
    'portraits'
  ]),
  created () {
    this.ttlImages = 0
  },
  methods: {
    onLoadHandler (index) {
      // console.log(index)

      console.log(index + ' : ' + this.indexHasBeenLoaded)

      if (index <= this.indexHasBeenLoaded) {
        this.indexHasBeenLoaded++
      } 

      // this.ttlLoaded++

      // currLoaded = 

      // load imgs in order (async)

      // ex:
      // load order 1,4,3,2,6,7,5

      // load 1
      // load 4, wait for 2

      // console.log(this.ttlImages + ' : ' + (this.portraits.length-1))
      // if (this.ttlImages === (this.portraits.length-1) && this.portraits.length !== 0) {
      //   this.allLoaded = true
      // } else {
      //   this.ttlImages++
      //   this.allLoaded = false
      // }
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
