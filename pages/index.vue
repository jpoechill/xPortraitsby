<template>
  <div>
    <transition name="fade" appear>
      <div class="container">
        <div class="row pt-1">
          <div v-for="(portrait, index) in portraits" :key="portrait.name" class="col-md-4 mb-2 pb-4">
              <nuxt-link :to="portrait.url">
                <transition name="fade" appear>
                  <img @load="onLoadHandler" v-show="ttlImages >= index" :src="portrait.thumbnail" class="w-100" alt="Portrait Tumbnail">
                </transition>
              </nuxt-link>
          </div>
        </div>
        <div class="row" v-show="isLoaded">
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
      isLoaded: false,
      ttlImages: 0
    }
  },
  computed: mapState([
    'portraits'
  ]),
  created () {
    this.ttlImages = 0
  },
  methods: {
    onLoadHandler (data) {
      // console.log('123')
      console.log(this.ttlImages + ' : ' + (this.portraits.length-1))
      if (this.ttlImages === (this.portraits.length-1) && this.portraits.length !== 0) {
        this.isLoaded = true
        console.log('Complete')
      } else {
        this.ttlImages++
        this.isLoaded = false
      }
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
