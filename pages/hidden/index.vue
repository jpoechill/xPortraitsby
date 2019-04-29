<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          Load Next Image: <button>Go</button>
        </div>
      </div>
      <div class="row">
        <div v-for="portrait in portraits" :key="portrait.name" class="col-md-4 bg-light p-2 mt-3 mb-3">
          Img Place Holder
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

.mh-custom {
  min-height: 240px;
}