<template>
  <div id="app" class="wrapper">
    <div class="content">
      <UserTable v-for="(table, i) of tableCount" :key="i" />
    </div>
  </div>
</template>

<script>
import UserTable from "@/components/UserTable/UserTable.vue";

export default {
  name: "App",

  components: {
    UserTable,
  },

  data() {
    return {
      tableCount: 2,
    };
  },
};
</script>

<style lang="css" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
.content {
  flex-grow: 1;
}
</style>
