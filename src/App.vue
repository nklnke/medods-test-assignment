<template>
  <div id="app">
    <div class="wrapper">
      <Header />
      <main>
        <InfoBlock />
        <FormWrapper />
      </main>
      <Sidebar />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Sidebar from "./components/Sidebar.vue";
import InfoBlock from "./components/InfoBlock.vue";
import FormWrapper from "./components/FormWrapper.vue";

export default {
  name: "App",
  components: {
    Header,
    Sidebar,
    InfoBlock,
    FormWrapper,
  },
};
</script>

<style lang="sass">
@import "./assets/styles/variables.sass"
@import "./assets/styles/typography.sass"
@import "./assets/styles/inputs.sass"
@import "./assets/styles/helpers.sass"

*,
*:before,
*:after
  box-sizing: border-box

*
  padding: 0
  margin: 0

body
  color: #434343
  background-color: #AFDAE8

#app
  font-family: Calibri, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  display: flex
  justify-content: center

.wrapper
  display: flex
  flex-flow: row wrap
  flex-basis: 1400px

  background-color: white

main
  order: 1
  flex: 3 0px

  padding: 48px 50px

aside
  order: 2
  flex: 1 auto
  padding: 50px 10px 15px 50px

  border-left: 1px solid lightgray
</style>
