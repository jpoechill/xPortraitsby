<template>
  <div>
    <div class="container">
      <div class="row pt-1 pb-4">
        <div class="col-md-9 pb-3">
          <img :src="currPortrait.hires" class="w-100" alt="Portrait Image">
        </div>
        <div class="col-md-3">
        <h4 class="font-weight-600">{{ currPortrait.title }}</h4> 
        <h4 class="font-weight-400">
          {{ currPortrait.description }} <br><br>
        </h4>
        <h4 class="font-weight-400">
          {{ currPortrait.finished }} <br><br>
        </h4><h4 class="font-weight-400">
          <!-- <hr> -->
          View Prev | Next
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
  transition: {
    appear: true,
    name: 'fade'
  }
}
</script>

<style>
</style>
