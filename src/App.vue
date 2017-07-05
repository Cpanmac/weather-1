<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
import Home from '@/components/home';

export default {
  name: 'app',
  components: {
    Home,
  },
};
</script>

<style lang="stylus">
@require 'style/rider'
/*normalize()*/
initialize()
body
  font-size: .16rem
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
