<template>
  <form
    class="add-client-form"
    accept-charset="UTF-8"
    action="action_page.php"
    autocomplete="off"
    method="GET"
    target="_blank"
    @submit.prevent="someAction()"
  >
    <h3>Общие данные</h3>

    <div class="surname">
      <label for="surname">Фамилия <span class="red">*</span></label>
      <input name="surname" type="text" />
    </div>

    <div class="name">
      <label for="name">Имя <span class="red">*</span></label>
      <input id="name" v-model="name" @blur="$v.name.$touch()" type="text" />
      <div class="error" v-if="$v.name.$error">
        <template v-if="!$v.name.maxLength">
          Длина имени не должна превышать
          {{ $v.name.$params.maxLength.max }} символов
        </template>
        <template v-else-if="!$v.name.alpha">
          Имя должно содержать только буквы
        </template>
        <template v-else>
          Имя обязательно для заполнения
        </template>
      </div>
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
      <input
        name="phone-number"
        type="text"
        placeholder="+7 (___) ___ - ____"
      />
    </div>

    <div class="sex">
      <label for="sex">Пол</label>
      <div class="">
        <!-- .flex-2 -->
        <input checked="checked" name="sex" type="radio" value="male" /> Мужской
        <input name="sex" type="radio" value="female" /> Женский
      </div>
    </div>

    <div class="client-group">
      <label for="client-group"
        >Группа клиентов <span class="red">*</span></label
      >
      <div class="">
        <!-- .flex-2 -->
        <input name="VIP" type="checkbox" /> VIP
        <input name="Проблемные" type="checkbox" /> Проблемные
        <input name="ОМС" type="checkbox" /> ОМС
      </div>
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

    <div class="index">
      <label for="index">Индекс</label>
      <input name="index" type="text" />
    </div>

    <div class="country">
      <label for="country">Страна</label>
      <input name="country" type="text" />
    </div>

    <div class="region">
      <label for="region">Область</label>
      <input name="region" type="text" />
    </div>

    <div class="town">
      <label for="town">Город <span class="red">*</span></label>
      <input name="town" type="text" />
    </div>

    <div class="street">
      <label for="street">Улица</label>
      <input name="street" type="text" />
    </div>

    <div class="house">
      <label for="house">Дом</label>
      <input name="house" type="text" />
    </div>

    <h3>Паспорт</h3>

    <div class="type-of-document">
      <label for="type-of-document">Тип документа</label>
      <select>
        <option selected="selected" value="1">Паспорт</option>
        <option value="2">Свидетельство о рождении</option>
        <option value="3">Вод. удостоверение</option>
      </select>
    </div>

    <div class="document-series">
      <label for="document-series">Серия</label>
      <input name="document-series" type="text" />
    </div>

    <div class="document-number">
      <label for="document-number">Номер</label>
      <input name="document-number" type="text" />
    </div>

    <div class="place-of-issue">
      <label for="place-of-issue">Кем выдан</label>
      <input name="place-of-issue" type="text" />
    </div>

    <div class="date-of-issue">
      <label for="date-of-issue">Дата выдачи <span class="red">*</span></label>
      <input name="date-of-issue" type="text" />
    </div>

    <button class="submit" type="submit" :disabled="$v.$invalid">
      Добавить
    </button>
  </form>
</template>

<script>
import { required, maxLength } from "vuelidate/lib/validators";

export default {
  data() {
    return {
      name: null,
    };
  },
  validations: {
    name: {
      required,
      maxLength: maxLength(10),
    },
  },
  methods: {
    someAction() {
      alert("Форма отправлена");
    },
  },
};
</script>

<style lang="sass" scoped>
.sex
  margin: 10px 0 20px

  input
    margin-left: 15px
    margin-right: 2px

.client-group
  display: flex
  align-items: center

  input
    margin-left: 15px
    margin-right: 2px

.submit
  padding: 12px 70px
  margin-top: 30px
  font-size: 24px
  cursor: pointer

  background-color: #5196FF
  color: white
  border: none
  border-radius: 5px

  &:hover
    background-color: #81B3FF
</style>
