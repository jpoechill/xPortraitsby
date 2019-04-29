<template>
  <div>
    <div class="container">
      <transition name="fade" appear>
        <div class="row mt-1">
          <div class="col-md-12">
            <transition name="fade" appear>
              <img :onLoad="onLoadHandler()" src="/background.jpg" v-show="isLoaded" class="w-100 pb-4" alt="About Image">
            </transition>
            <div v-show="!isLoaded" class="panel mb-4 bg-custom text-center">
              <span class="font-custom">PR</span>
            </div>
            <h4 class="font-weight-400 pb-5">
              Po Rith has been drawing for a really long time. Recently though, he's gotten into portraits and watercolors. 
              <br><br>
              You can follow him on <a href="https://instagram.com/jpoechill">Instagram</a>, or send him a <nuxt-link to="contact">message</nuxt-link>.
            </h4>
          </div>
        </div>
      </transition>
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
export default {
  data: function () {
    return {
      background: '',
      isLoaded: false,
    }
  },
  methods: {
    onLoadHandler (data) {
      this.isLoaded = true
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
  display: flex;
  min-height: 460px;
  /* height: 100%; */
  justify-content: center;
  align-items: center;
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
