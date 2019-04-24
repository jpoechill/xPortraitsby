<template>
  <div>
    <div class="container">
      <div class="row pt-1">
        <div v-for="portrait in portraits" :key="portrait.name" class="col-md-4 mb-2 pb-4 bg-light">
          <div>
            <nuxt-link :to="portrait.url">
              <img :src="portrait.thumbnail" class="w-100" alt="Portrait Tumbnail">
            </nuxt-link>
          </div>
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
  computed: mapState([
    'portraits'
  ]),
  transition: {
    appear: true,
    name: 'fade'
  }
}
</script>

<style>
</style>
