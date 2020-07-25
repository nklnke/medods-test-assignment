<template>
  <div id="app">
    <div class="wrapper">
      <header>
        <ul class="menu">
          <li>
            <img src="./assets/images/logo.svg" />
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

      <main>
        <h1>Добавить клиента</h1>

        <h5>
          Поля, отмеченные <span class="red">*</span>, обязательны для
          заполнения
        </h5>

        <form
          class="add-client-form"
          accept-charset="UTF-8"
          action="action_page.php"
          autocomplete="off"
          method="GET"
          target="_blank"
        >
          <h3>Общие данные</h3>

          <div class="surname">
            <label for="surname">Фамилия <span class="red">*</span></label>
            <input name="surname" type="text" />
          </div>

          <div class="name">
            <label for="name">Имя <span class="red">*</span></label>
            <input name="name" type="text" />
          </div>

          <div class="patronymic">
            <label for="patronymic">Отчество</label>
            <input name="patronymic" type="text" />
          </div>

          <div class="birthday">
            <label for="birthday">Дата рождения <span class="red">*</span></label>
            <input name="birthday" type="text" placeholder="__.__.____" />
          </div>

          <div class="phone-number">
            <label for="phone-number">Номер телефона</label>
            <input name="phone-number" type="text" placeholder="+7 (___) ___ - ____" />
          </div>

          <div class="sex">
            <label for="sex">Пол</label>
            <input checked="checked" name="sex" type="radio" value="male" /> Мужской
            <input name="sex" type="radio" value="female" /> Женский
          </div>

          <div class="client-group">
            <label for="client-group">Группа клиентов <span class="red">*</span></label>
            xxxxx
          </div>

          <div class="doctor">
            <label for="doctor">Лечащий врач</label>
            <select>
              <option selected="selected" value="1">Иванов</option>
              <option value="2">Захаров</option>
              <option value="3">Чернышева</option>
            </select>
          </div>

          <div class="sms-checkbox">
            <input name="sms-checkbox" type="checkbox" checked />
            <label for="sms-checkbox">Не отправлять СМС</label>
          </div>

          <h3>Адрес</h3>

          <h3>Паспорт</h3>

          <button class="submit" type="submit">Добавить</button>
        </form>
      </main>

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
  width: 1400px

  background-color: white

header
  width: 100%
  height: 80px
  flex: 1 100%

  background-color: #81B3FF

.menu
  list-style: none
  display: flex
  height: 100%
  align-items: center

  li
    padding: 28px 20px
    cursor: pointer

    &:hover
      background-color: #5196FF
      a
        color: #A4C7E6

    &:first-child
      margin-left: 50px

      &:hover
      background-color: transparent

    a
      font-size: 20px
      text-decoration: none
      color: white

main
  order: 1
  flex: 3 0px

  padding: 48px 110px

.sex
  margin: 20px 0 40px

.submit
  padding: 12px 70px
  font-size: 24px
  cursor: pointer

  background-color: #5196FF
  color: white
  border: none
  border-radius: 5px

  &:hover
    background-color: #81B3FF

aside
  order: 2
  flex: 1 auto
  padding: 50px 10px 15px 50px

  border-left: 1px solid lightgray

  ul
    list-style: none
    margin-left: 0

    li
      margin-bottom: 15px
      font-size: 24px

      &:first-child
        margin-top: 15px

</style>
