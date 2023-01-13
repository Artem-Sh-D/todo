<template>
  <div v-if="posts.length > 0" class="wrapper">
    <v-card
      class="ma-3"
      v-for="post in posts"
      :key="post.id"
      @remove="$emit('remove', post)"
    >
      <v-card-title>
        {{ post.title }}
      </v-card-title>
      <v-card-text>
        {{ post.body }}
      </v-card-text>
      <v-card-actions class="justify-center">
        <v-btn @click="$emit('remove', post)">Удалить заметку</v-btn>
        <v-btn v-if="!post.favorite" @click="$emit('addfavorite', post)">
          Добавить в избранное</v-btn
        >
        <v-btn v-else @click="$emit('deletefavorite', post)"
          >Удалить из избранного</v-btn
        >
      </v-card-actions>
    </v-card>
  </div>
  <div v-else class="ma-5 w-100 h-100">
    <h2>У вас еще нет заметок</h2>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Note",
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  methods: {},
};
</script>

<style scoped></style>
