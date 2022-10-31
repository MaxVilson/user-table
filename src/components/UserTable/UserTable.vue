<template>
  <b-table-simple>
    <b-thead>
      <b-tr>
        <b-td v-for="(header, i) of $options.headers" :key="`${header}-${i}`">{{
          header
        }}</b-td>
      </b-tr>
    </b-thead>
    <b-tbody>
      <b-tr v-for="(user, i) of users" :key="i">
        <b-td>
          <b-form-input v-model.lazy="user.fullName"></b-form-input>
        </b-td>
        <b-td>
          <b-form-datepicker
            v-model="user.dateOfBirth"
            class="mb-2"
          ></b-form-datepicker>
        </b-td>
        <b-td>
          <b-form-select
            v-model="user.favoriteBook"
            :options="$options.optionsBooks"
          ></b-form-select>
        </b-td>
        <b-td>
          <b-form-radio
            v-for="item of $options.genders"
            v-model="user.gender"
            :key="item"
            :value="item"
            name="gender"
            >{{ item }}</b-form-radio
          >
        </b-td>
        <b-td>
          <b-form-select
            v-model="user.skills"
            :options="$options.optionsSkills"
            multiple
            :select-size="4"
          ></b-form-select>
        </b-td>
      </b-tr>
    </b-tbody>
  </b-table-simple>
</template>

<script>
import {
  BTableSimple,
  BThead,
  BTbody,
  BTr,
  BTd,
  BFormInput,
  BFormDatepicker,
  BFormSelect,
  BFormRadio,
} from "bootstrap-vue";

const headers = Object.freeze([
  "Фамилия И.О.",
  "Дата рождения",
  "Любимая книга",
  "Пол",
  "Навыки",
]);
const optionsBooks = Object.freeze([
  { value: "antikhrupkost", text: "Антихрупкость" },
  {
    value: "fenix",
    text: "Проект «Феникс». Роман о том, как DevOps меняет бизнес к лучшему",
  },
  { value: "1984", text: "1984" },
]);
const genders = Object.freeze(["Male", "Female"]);
const optionsSkills = Object.freeze(["js", "vue", "html", "css"]);
const rowsCount = 3;

export default {
  headers,
  optionsBooks,
  genders,
  optionsSkills,
  rowsCount,

  components: {
    BTableSimple,
    BThead,
    BTbody,
    BTr,
    BTd,
    BFormInput,
    BFormDatepicker,
    BFormSelect,
    BFormRadio,
  },

  data() {
    return {
      users: [
        {
          fullName: "",
          dateOfBirth: "",
          favoriteBook: "",
          gender: "",
          skills: [],
        },
        {
          fullName: "",
          dateOfBirth: "",
          favoriteBook: "",
          gender: "",
          skills: [],
        },
        {
          fullName: "",
          dateOfBirth: "",
          favoriteBook: "",
          gender: "",
          skills: [],
        },
      ],
    };
  },
};
</script>
