<template>
  <div>
    <div id="blog">
      <div v-if="allPosts">
        <li v-for="(post, idx) in allPosts.slice().reverse()" :key="idx">
          <h3>{{ post.title }}</h3>
          <h5>{{ post.timeOfPost.toDate().toDateString() }}</h5>
          <p>{{ post.post }}</p>
          <!--<button id="likes" @click="like(post)">Like! ({{ post.likes }})</button>-->
        </li>
      </div>
    </div>
    <NewPost v-if="auth" />
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
import NewPost from "../components/NewPost.vue";

export default {
  name: "Blog",
  components: {
    NewPost,
  },
  methods: {
    ...mapActions(["getPosts", "newLike"]),
    like(post) {
      console.log(post);
      this.newLike(post.id);
    },
  },
  computed: {
    ...mapGetters(["allPosts", "auth"]),
  },
  created() {
    this.getPosts().then(console.log("posts fetched"));
  },
};
</script>

<style>
#blog {
  margin: auto;
  padding: 5%;
}
#likes {
  border-style: outset;
  background-color: aqua;
  border-color: lightblue;
}
</style>

<style scoped>
h5 {
  font-style: italic;
}
</style>