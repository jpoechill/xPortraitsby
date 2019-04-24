<template>
  <div>
    <div class="container">
      <div class="row pt-1 pb-4">
        <div class="col-md-8 pb-3">
          <img :src="currPortrait.hires" class="w-100" alt="Portrait Image">
        </div>
        <div class="col-md-4">
        <h4 class="font-weight-600">{{ currPortrait.title }}</h4> 
        <h4 class="font-weight-400">
          {{ currPortrait.description }} <br><br>
        </h4>
        <h4 class="font-weight-400">
          {{ currPortrait.finished }} <br><br>
        </h4><h4 class="font-weight-400">
          <!-- <hr> -->
          <nuxt-link to="" @click.native.prevent="goPrev()">Prev</nuxt-link> | 
          <nuxt-link to="" @click.native.prevent="goNext()">Next</nuxt-link>
        </h4>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-md-12 text-right">
          <h4>© 2019</h4>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { mapState } from 'vuex'

export default {
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
  methods: {
    goPrev: function () {
      let portraits = this.portraits
      let index = this.findIndex(this.$route.params.model)

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
    }
  },
  transition: {
    appear: true,
    name: 'fade'
  }
}
</script>

<style>
.fake-link {
  font-weight: 600;
}

.fake-link:hover {
  cursor: pointer;
}
</style>
