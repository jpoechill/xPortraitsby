<template>
  <div>
    <div class="container">
      <div class="row pt-1 pb-4">
        <div  class="col-md-8 pb-3">
          <transition name="fade" appear>
            <img :onLoad="loadHandler()" :src="currPortrait.hires" v-show="isLoaded" class="w-100" alt="Portrait Image">
          </transition>
          <div v-show="!isLoaded" class="panel w-100 bg-custom text-center">
            <span class="font-custom">PR</span>
          </div>
        </div>
        <div class="col-md-4">
        <div class="mh-custom">
          <h4 class="font-weight-600">{{ currPortrait.title }}</h4> 
          <h4 class="font-weight-400">
            {{ currPortrait.description }} <br>
          </h4>
          <h4 class="font-weight-400 text-right">
            {{ currPortrait.finished }} <br><br>
          </h4>
        </div>
        <h4 class="font-weight-400">
          <nuxt-link to="" @click.native.prevent="goPrev()">Prev</nuxt-link> | 
          <nuxt-link to="" @click.native.prevent="goNext()">Next</nuxt-link>
        </h4>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-md-12 mb-3 text-right">
          <h4>© 2019</h4>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { mapState } from 'vuex'

export default {
  data () { 
    return {
      isLoaded: false
    }
  },
  computed: {
    currPortrait () {
      let self = this
      let hello = 123
      let model = this.$route.params.model

      let arr = this.portraits

      let selected = arr.find(function(item){
        return item.name === model
      })

      return selected
    },
    ...mapState([
      'portraits'
    ])
  },
  created() {
    this.isLoaded = false
  },
  methods: {
    goPrev: function () {
      let portraits = this.portraits
      let index = this.findIndex(this.$route.params.model)

      this.isLoaded = false

      if (index === 0) {
        index = (portraits.length-1)
      } else {
        index--
      }

      this.$router.push(portraits[index].url)
    },
    goNext: function () {
      let portraits = this.portraits
      let index = this.findIndex(this.$route.params.model)

      this.isLoaded = false

      if (index < (portraits.length-1)) {
        index++
      } else {
        index = 0
      }

      this.$router.push(portraits[index].url)
    },
    findIndex: function (model) {
      let currIndex

      this.portraits.forEach(function(item, index){
        if (item.name === model) {
          currIndex = index
        }
      })

      return currIndex
    },
    loadHandler () {
      let self = this 

      self.isLoaded = true
    }
  },
  transition: {
    appear: true,
    name: 'fade'
  }
}
</script>

<style scoped>
.panel {
  display: flex;
  justify-content: center;
  align-items: center;
}

@media only screen and (min-width : 768px) {
  .panel {
    min-height: 600px;
  }
}

@media only screen and (min-width : 992px) {
  .panel {
    min-height: 700px;
  }
}

@media only screen and (min-width : 1200px) {
  .panel {
    min-height: 800px;
  }
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

.fake-link {
  font-weight: 600;
}

.fake-link:hover {
  cursor: pointer;
}

.mh-custom {
  min-height: 240px;
}
</style>
