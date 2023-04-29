@@ -1,98 +0,0 @@
<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <MyButton @click="showDialog">
      создать пост
    </MyButton>
    <MyDialog v-model:show="dialogVisible">
      <PostForm @create="createPost" />
    </MyDialog>
    <PostList :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue"
import PostList from "@/components/PostList.vue"
import MyDialog from "./components/UI/MyDialog.vue";
import MyButton from "./components/UI/MyButton.vue";
export default {
  components: {
    PostList,
    PostForm,
    MyDialog,
    MyButton
},
  data() {
    return {
      posts: [
        { id: 1, title: 'JavaScript', body: 'JS - язык программирования' },
        { id: 2, title: 'Чай', body: 'Чай - единственный допустимый напиток' },
        { id: 3, title: 'УдГУ', body: 'УдГУ - вроде как вуз' },
      ],
      dialogVisible: false
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px
}
</style>
