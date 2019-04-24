<template>
  <div>
    <div class="container">
      <transition name="fade" appear>
        <div class="row pt-1">
          <div class="col-md-12">
            <img src="background.jpg" class="w-100 pb-4" alt="About Image">
            <h4 class="font-weight-400 pb-5">
              Po Rith has been drawing for a really long time. Recently though, he's gotten into portraits and watercolors. 
              <br><br>
              Follow him on <a href="https://instagram.com/jpoechill">Instagram</a>, or send him a <nuxt-link to="contact">message</nuxt-link>.
            </h4>
          </div>
        </div>
      </transition>
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
export default {
  transition: {
    appear: true,
    name: 'fade'
  }
}
</script>

<style>
</style>
