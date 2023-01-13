<template>
  <v-card>
    <v-text-field
      v-model="post.title"
      label="Введите заголовок"
      variant="solo"
    ></v-text-field>
    <v-textarea v-model="post.body" label="Введите текст" variant="solo">
    </v-textarea>
    <v-btn class="ma-3" @click="addPosts">Создать заметку</v-btn>
  </v-card>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Form",
  data() {
    return {
      post: {
        title: "",
        body: "",
        favorite: false,
      },
    };
  },
  methods: {
    addPosts() {
      if (!(this.post.title === "") && !(this.post.body === "")) {
        this.post.id = Date.now();
        this.$emit("create", this.post);
        this.post = {
          title: "",
          body: "",
        };
      } else {
        alert("Поле заголовка и поле заметки не должно быть пустым");
      }
    },
  },
};
</script>

<style scoped></style>
