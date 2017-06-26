<template>
  <div id="app">
    <div class="row">
      <div class="col-lg-3 col-lg-offset-3">
        <h1>L2 Manor Calculator</h1>
        <h5>by Cujo</h5>
      </div>
    </div>
    <div class="row">
      <div class="col-lg-6 col-lg-offset-3 col-md-12">
        <manor></manor>
      </div>
    </div>
  </div>
</template>

<script>
import Manor from 'components/Manor'

export default {
  name: 'app',
  components: {
    manor: Manor
  }
}
</script>

<style lang="scss">
  @import './assets/styles/app.scss';
</style>
