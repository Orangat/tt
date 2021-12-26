<template>
  <div id="app">
    <o-game />
  </div>
</template>

<script>
import OGame from '@/components/organisms/o-game'

export default {
  name: 'App',
  components: {
    OGame
  }
}
</script>

<style lang="scss">
@import "src/css/variables.scss";

#app {
  font-family: "Inter","Helvetica Neue","Segoe UI","Fira Sans",Roboto,Oxygen,Ubuntu,"Droid Sans","Arial",sans-serif;
  text-align: center;
  color: $color-black;
}
</style>
