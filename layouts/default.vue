<template>
  <div class="fadein-custom">
    <!-- Start Desktop -->
    <div class="container d-none d-md-block">
      <div class="row font-weight-bold mt-4 mb-4 pt-3">
        <div class="col-md-6">
          <nuxt-link to="/">
            <img src="~static/logo.png" class="logo" alt="PR Logo">
          </nuxt-link>
        </div>
        <div class="col-md-6 d-flex justify-content-end align-items-center font-weight-600 word-spacing">
          <h4>
            <nuxt-link to="/about">about</nuxt-link>
            <nuxt-link to="/">portraits</nuxt-link>
            <nuxt-link to="/contact">contact</nuxt-link>
          </h4>
        </div>
      </div>
    </div>
    <!-- Start Mobile -->
    <div class="container d-md-none">
      <div class="row font-weight-bold mt-1 mb-2 pt-3">
        <div class="col-md-6 text-center">
          <nuxt-link to="/">
            <img src="~static/logo.png" class="w-25 logo mb-3" alt="PR Logo">
          </nuxt-link>
        </div>
        <div class="col-md-6 text-center font-weight-600 word-spacing">
          <h4>
            <nuxt-link to="/about">about</nuxt-link>
            <nuxt-link to="/">portraits</nuxt-link>
            <nuxt-link to="/contact">contact</nuxt-link>
          </h4>
        </div>
      </div>
    </div>

    <!-- Start Nuxt Body -->
    <nuxt />
    <!-- End Nuxt Body -->
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      isActive: true
    }
  },
  transition: {
    appear: true,
    name: 'fade'
  }
}
</script>

<style>
html {
  font-family: 'Helvetica Neue', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto,  Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

html, body {
  background-color: #FBFBFB;
}

a {
  color: #111;
}

a:hover {
  color: #666;
}

.pb-100 {
  padding-bottom: 100%;
}

.pr-30 {
  padding-right: 30px;
}

.logo {
  width: 72px;
}

.font-weight-600 {
  font-weight: 600;
}

.font-weight-400 {
  font-weight: 400;
}

.word-spacing {
  word-spacing: 8px;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}

.fade-enter, .fade-leave-to, .fade-leave-active {
  opacity: 0;
}

.long-fade-enter-active, .long-fade-leave-active {
  transition: opacity 3s;
}

.long-fade-enter, .long-fade-leave-to, .long-fade-leave-active {
  opacity: 0;
}

.fadein-custom {
  -webkit-animation: fadein 2s; /* Safari, Chrome and Opera > 12.1 */
      -moz-animation: fadein 2s; /* Firefox < 16 */
      -ms-animation: fadein 2s; /* Internet Explorer */
        -o-animation: fadein 2s; /* Opera < 12.1 */
          animation: fadein 2s;
}

@keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Firefox < 16 */
@-moz-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Safari, Chrome and Opera > 12.1 */
@-webkit-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Internet Explorer */
@-ms-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Opera < 12.1 */
@-o-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}
</style>
