<template>
  <aside>
    <h1>Sidebar</h1>

    <ul>
      <li>sidebar-item</li>
      <li>sidebar-item</li>
      <li>sidebar-item</li>
      <li>sidebar-item</li>
      <li>sidebar-item</li>
      <li>sidebar-item</li>
      <li>sidebar-item</li>
    </ul>
  </aside>
</template>

<script>
export default {};
</script>

<style lang="sass" scoped>
ul
  list-style: none
  margin-left: 0

  li
    margin-bottom: 15px
    font-size: 24px

    &:first-child
      margin-top: 15px
</style>
