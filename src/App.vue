<template>
  <div id="app">
    <app-modal></app-modal>
  </div>
</template>

<script>
  import AppModal from './components/AppModal'

  export default {
    name: 'app',
    components: {
      AppModal
    },
    data() {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    }
  }
</script>

<style lang="scss">
  @import "scss/style.scss";

  #app {
    padding: 16px;
    font-family: Arimo, sans-serif;
    color: $clr-dark;
  }

</style>
