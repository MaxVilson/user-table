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
      <b-tr>
        <b-td>
          <b-form-input v-model.lazy="fullName"></b-form-input>
        </b-td>
        <b-td>
          <b-form-datepicker
            v-model="dateOfBirth"
            class="mb-2"
          ></b-form-datepicker>
        </b-td>
        <b-td>
          <b-form-select
            v-model="favoriteBook"
            :options="$options.optionsBooks"
          ></b-form-select>
        </b-td>
        <b-td>
          <b-form-radio
            v-for="item of $options.genders"
            v-model="gender"
            :key="item"
            :value="item"
            name="gender"
            >{{ item }}</b-form-radio
          >
        </b-td>
        <b-td>
          <b-form-select
            v-model="skills"
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

export default {
  headers,
  optionsBooks,
  genders,
  optionsSkills,

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
      fullName: "",
      dateOfBirth: "",
      favoriteBook: "",
      gender: "",
      skills: [],
    };
  },
};
</script>
