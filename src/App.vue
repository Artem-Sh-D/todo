<template>
  <v-app :theme="theme">
    <v-app-bar title="Todo List">
      <v-spacer></v-spacer>
      <v-btn
        :prepend-icon="
          theme === 'light' ? `mdi-weather-sunny` : `mdi-weather-night`
        "
        @click="switchTheme"
        >Сменить тему</v-btn
      >
    </v-app-bar>

    <v-main>
      <v-container>
        <Form @create="createPost" />
        <Note
          @deletefavorite="deleteFavorite"
          @addfavorite="addFavorite"
          @remove="removePost"
          v-bind:posts="posts"
        />
      </v-container>
    </v-main>
    <v-footer :theme="theme" :elevation="15">
      <Footer />
    </v-footer>
  </v-app>
</template>
<script>
import Footer from "@/components/Footer.vue";
import Note from "@/components/Note.vue";
import Form from "@/components/Form.vue";

export default {
  components: { Form, Note, Footer },
  data() {
    return {
      posts: [],
      theme: "light",
    };
  },
  methods: {
    switchTheme() {
      this.theme === "light" ? (this.theme = "dark") : (this.theme = "light");
    },
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    addFavorite(post) {
      post.favorite = true;
      this.posts = this.posts.filter((p) => p.id !== post.id);
      this.posts.unshift(post);
    },
    deleteFavorite(post) {
      post.favorite = false;
      this.posts = this.posts.filter((p) => p.id !== post.id);
      this.posts.push(post);
    },
  },
};
</script>

<style></style>
