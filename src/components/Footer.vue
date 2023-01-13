<template>
  <v-row justify="center" no-gutters>
    <v-btn
      v-for="link in links"
      :key="link"
      theme="light"
      variant="text"
      class="mx-2"
      rounded="xl"
    >
      {{ link }}
    </v-btn>
    <v-col class="text-center mt-4" cols="12">
      {{ new Date().getFullYear() }} — <strong>Todo List</strong>
    </v-col>
  </v-row>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Footer",
  data() {
    return {
      links: ["Telegram", "Vk", "Github", "Mail"],
    };
  },
};
</script>

<style scoped></style>
