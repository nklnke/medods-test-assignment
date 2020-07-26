<template>
  <header>
    <ul class="menu">
      <li>
        <img src="./../assets/images/logo.svg" />
      </li>
      <li>
        <a class="nav__link" href="#">Главная</a>
      </li>
      <li>
        <a class="nav__link" href="#">Список клиентов</a>
      </li>
      <li>
        <a class="nav__link" href="#">Добавить клиента</a>
      </li>
    </ul>
  </header>
</template>

<script>
export default {};
</script>

<style lang="sass" scoped>
header
  flex: 1 100%

  background-color: #81B3FF

.menu
  list-style: none
  display: flex
  flex-wrap: wrap
  align-items: center

  li
    padding: 28px 20px
    cursor: pointer

    &:hover
      background-color: #5196FF
      a
        color: #A4C7E6

    &:first-child
      padding: 0
      margin-right: 20px
      margin-left: 50px

      &:hover
      background-color: transparent

    a
      font-size: 20px
      text-decoration: none
      color: white
</style>
