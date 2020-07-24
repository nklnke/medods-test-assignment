<template>
  <div id="app">
    <div class="wrapper">
      <header>
        header
      </header>
      <main>
        main
      </main>
      <aside>
        aside
      </aside>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
};
</script>

<style lang="sass">
@import "./assets/styles/variables.sass";

*
  padding: 0
  margin: 0

.flex
  display: flex

body
  color: #2c3e50
  background-color: #AFDAE8

#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  display: flex
  justify-content: center

.wrapper
  display: flex
  flex-flow: row wrap
  width: 1400px
  padding: $margin*2

  background-color: white

header
  height: 80px
  flex: 1 100%

  background-color: #81B3FF

main
  order: 1
  flex: 3 0px
  background-color: green

aside
  order: 2
  flex: 1 auto
  background-color: yellow
</style>
