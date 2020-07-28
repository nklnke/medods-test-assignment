<template>
  <form
    class="add-client-form"
    accept-charset="UTF-8"
    action="action_page.php"
    method="GET"
    @submit.prevent="submit()">

    <h3>Общие данные</h3>

    <!-- surname check -->
    <div class="form-group surname" :class="{ 'form-group__error': $v.name.$error }">
      <label class="form-group__label" for="surname">Фамилия <span class="red">*</span></label>
      <input class="form-group__input" v-model.trim="$v.surname.$model" type="text" />
    </div>
    <div class="error" v-if="!$v.surname.required">Фамилия обязательна</div>

    <!-- name check -->
    <div class="form-group name" :class="{ 'form-group__error': $v.name.$error }">
      <label class="form-group__label" for="name">Имя <span class="red">*</span></label>
      <input class="form-group__input" v-model.trim="$v.name.$model" type="text" />
    </div>
    <div class="error" v-if="!$v.name.required">Имя обязательно</div>

    <!-- patronymic WITHOUT check-->
    <div class="form-group patronymic">
      <label class="form-group__label" for="patronymic">Отчество</label>
      <input class="form-group__input" type="text" />
    </div>

    <!-- birthday check -->
    <div class="form-group birthday" :class="{ 'form-group__error': $v.birthday.$error }">
      <label class="form-group__label" for="birthday">Дата рождения <span class="red">*</span></label>
      <input class="form-group__input" v-model.trim="$v.birthday.$model" type="text" placeholder="__.__.____" />
    </div>
    <div class="error" v-if="!$v.birthday.required">Дата рождения обязательна</div>

    <!-- phone-number check -->
    <div class="form-group phone-number" :class="{ 'form-group__error': $v.phoneNumber.$error }">
      <label class="form-group__label" for="phoneNumber">Номер телефона</label>
      <input class="form-group__input" v-model.trim="$v.phoneNumber.$model" type="text" placeholder="+7 (___) ___ - ____" />
    </div>
    <div class="error" v-if="!$v.phoneNumber.required">Номер должен содержать 11 цифр</div>

    <!-- sex WITHOUT check -->
    <div class="form-group sex">
      <label class="form-group__label" for="sex">Пол</label>
      <div>
        <input checked="checked" name="sex" type="radio" value="male" /> Мужской
        <input name="sex" type="radio" value="female" /> Женский
      </div>
    </div>

    <!-- client-group check -->
    <div class="form-group client-group" :class="{ 'form-group__error': $v.clientGroup.$error }">
      <label class="form-group__label" for="client-group">Группа клиентов <span class="red">*</span></label>
      <div class="">
        <!-- TODO: разобраться с проверкой мультиселектора -->
        <!-- !$v.clientGroup1.required -->
        <!-- !$v.clientGroup2.required -->
        <!-- !$v.clientGroup3.required -->
        <!-- один из них должен сработать, тогда проверка пройдёт -->
        <input name="VIP" type="checkbox" v-model="$v.clientGroup.$model" /> VIP
        <input name="Проблемные" type="checkbox" v-model="$v.clientGroup.$model" /> Проблемные
        <input name="ОМС" type="checkbox" v-model="$v.clientGroup.$model" /> ОМС
      </div>
    </div>
    <div class="error" v-if="!$v.clientGroup.required">Обязательно для заполнения</div>

    <!-- doctor WITHOUT check -->
    <div class="form-group doctor">
      <label class="form-group__label" for="doctor">Лечащий врач</label>
      <select>
        <option selected="selected" value="1">Иванов</option>
        <option value="2">Захаров</option>
        <option value="3">Чернышева</option>
      </select>
    </div>

    <!-- sms-check WITHOUT check -->
    <div class="form-group sms-check">
      <input name="sms-checkbox" type="checkbox" checked />
      <!-- TODO: сделать отступ от галочки -->
      <label class="form-group__label" for="sms-check">Не отправлять СМС</label>
    </div>

    <h3>Адрес</h3>

    <!-- index WITHOUT check-->
    <div class="form-group index">
      <label class="form-group__label" for="index">Индекс</label>
      <input class="form-group__input" type="text" />
    </div>

    <!-- country WITHOUT check-->
    <div class="form-group country">
      <label class="form-group__label" for="country">Страна</label>
      <input class="form-group__input" type="text" />
    </div>

    <!-- region WITHOUT check-->
    <div class="form-group region">
      <label class="form-group__label" for="region">Область</label>
      <input class="form-group__input" type="text" />
    </div>
  
    <!-- town check -->
    <div class="form-group town" :class="{ 'form-group__error': $v.town.$error }">
      <label class="form-group__label" for="town">Город <span class="red">*</span></label>
      <input class="form-group__input" v-model.trim="$v.town.$model" type="text" />
    </div>
    <div class="error" v-if="!$v.town.required">Город обязателен</div>

    <!-- street WITHOUT check-->
    <div class="form-group street">
      <label class="form-group__label" for="street">Область</label>
      <input class="form-group__input" type="text" />
    </div>

    <!-- house WITHOUT check-->
    <div class="form-group house">
      <label class="form-group__label" for="house">Дом</label>
      <input class="form-group__input" type="text" />
    </div>

    <h3>Паспорт</h3>

    <!-- type-of-document check -->
    <div class="form-group type-of-document" :class="{ 'form-group__error': $v.typeOfDocument.$error }">
      <label class="form-group__label" for="typeOfDocument">Тип документа <span class="red">*</span></label>
      <select v-model.trim="$v.typeOfDocument.$model">
        <option selected="selected" value="1">Паспорт</option>
        <option value="2">Свидетельство о рождении</option>
        <option value="3">Вод. удостоверение</option>
      </select>
    </div>
    <div class="error" v-if="!$v.typeOfDocument.required">Типа документа обязателен</div>

    <!-- document-series WITHOUT check-->
    <div class="form-group document-series">
      <label class="form-group__label" for="document-series">Серия</label>
      <input class="form-group__input" type="text" />
    </div>

    <!-- document-number WITHOUT check-->
    <div class="form-group document-number">
      <label class="form-group__label" for="document-number">Номер</label>
      <input class="form-group__input" type="text" />
    </div>

    <!-- place-of-issue WITHOUT check-->
    <div class="form-group place-of-issue">
      <label class="form-group__label" for="place-of-issue">Кем выдан</label>
      <input class="form-group__input" type="text" />
    </div>

    <!-- date-of-issue check -->
    <div class="form-group date-of-issue" :class="{ 'form-group__error': $v.dateOfIssue.$error }">
      <label class="form-group__label" for="date-of-issue">Дата выдачи <span class="red">*</span></label>
      <input class="form-group__input" v-model.trim="$v.dateOfIssue.$model" type="text" placeholder="__.__.____" />
    </div>
    <div class="error" v-if="!$v.dateOfIssue.required">Дата выдачи обязательна</div>

    <button class="submit" type="submit" :disabled="submitStatus === 'PENDING'">Добавить</button>

    <p class="submitStatus green" v-if="submitStatus === 'OK'">Клиент успешно добавлен</p>
    <p class="submitStatus red" v-if="submitStatus === 'ERROR'">Пожалуйста, правильно заполните все поля</p>
    <p class="submitStatus blue" v-if="submitStatus === 'PENDING'">Добавление...</p>
  </form>
</template>

<script>
import { required, minLength, maxLength } from "vuelidate/lib/validators";

export default {
  data() {
    return {
      surname: "",
      name: "",
      birthday: "",
      phoneNumber: "",
      clientGroup: "",
      doctor: "",
      town: "",
      typeOfDocument: "",
      dateOfIssue: "",
      submitStatus: null
    };
  },
  validations: {
    surname: {
      required
    },
    name: {
      required
    },
    birthday: {
      required
    },
    phoneNumber: {
      minLength: minLength(11),
      maxLength: maxLength(11)
    },
    clientGroup: {
      required
    },
    town: {
      required
    },
    typeOfDocument: {
      required
    },
    dateOfIssue: {
      required
    }
  },
  methods: {
    submit() {
      this.$v.$touch();
      if (this.$v.$invalid) {
        this.submitStatus = "ERROR";
      } else {
        console.log("Клиент добавлен");
        this.submitStatus = "PENDING";
        setTimeout(() => {
          this.submitStatus = "OK";
        }, 500);
      }
    },
  },
};
</script>

<style lang="sass" scoped>
.sex
  margin: 10px 0 20px

  input
    margin-left: 20px
    margin-right: 5px

.client-group
  height: 80px

  input
    margin-left: 20px
    // margin-right: 5px

.submit
  padding: 12px 70px
  margin-top: 30px
  font-size: 24px
  cursor: pointer

  background-color: #5196FF
  color: white
  border: none
  border-radius: 5px

  transition: .2s ease

  &:hover
    background-color: #81B3FF

  &:disabled
    background-color: lightgray
    cursor: not-allowed

.error
  position: relative
  top: -25px

.submitStatus
  font-size: 24px
  display: inline-block
  margin-left: 20px
</style>
