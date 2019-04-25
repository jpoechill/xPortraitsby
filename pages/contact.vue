<template>
  <div>
    <div class="container">
      <div class="row pt-1">
        <div class="col-md-12">
          <h4 class="font-weight-400 pb-3">
            Questions? Send an email directly to <a href="mailto:heys@rithfolio.com">heys@rithfolio.com</a>, or kindly leave a message below.
          </h4>
        </div>
      </div>
      <div class="row">
        <div class="col-md-6">
          <form action="https://formspree.io/heys@rithfolio.com" method="POST">
            <input type="text" class="form-control-lg" name="name" placeholder="Name"><br><br>
            <input type="text" class="form-control-lg" name="email" placeholder="Email"><br><br>
            <textarea class="form-control-custom" cols="30" rows="6" name="message" placeholder="Message"></textarea>
            <button type="submit" class="btn btn-lg btn-dark mt-3">Send Message</button>
          </form>
          
        </div>
        <div class="col-md-6">
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
export default {
  transition: 'fade'
}
</script>

<style>
a {
  font-weight: 500;
}

.form-control-lg, textarea {
  width: 100%;
}

.form-control-custom {
  padding: .5rem 1rem;
  font-size: 1.25rem;
  line-height: 1.5;
  border-radius: .3rem;
}
</style>
