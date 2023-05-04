@@ -1,98 +0,0 @@
<template>
  <div>
    <h1>Страница с постами</h1>
    <MyInput v-model="searchQuery" placeholder="Поиск....." />
    <div class="app__btns">
      <MyButton @click="showDialog">
        Создать пост
      </MyButton>
      <MySelect v-model="selectedSort" :options="sortOptions" />
    </div>
    <MyDialog v-model:show="dialogVisible">
      <PostForm @create="createPost" />
    </MyDialog>
    <PostList :posts="sortedAndSearchedPosts" @remove="removePost" v-if="!isPostsLoading" />
    <h2 v-else>Идет загрузка...</h2>
    <div v-intersection="loadMorePosts" class="observer"></div>
  </div>
</template>

<script>
import axios from 'axios'
import PostForm from "@/components/PostForm.vue"
import PostList from "@/components/PostList.vue"
import usePosts from "@/hooks/usePosts";
import useSortedPosts from "@/hooks/useSortedPosts";
import useSortedAndSearchedPosts from "@/hooks/useSortedAndSearchedPosts";

export default {
  components: {
    PostList,
    PostForm,
  },
  data() {
    return {
      dialogVisible: false,
      page: 1,
      limit: 10,
      sortOptions: [
        { value: 'title', name: 'По названию' },
        { value: 'body', name: 'По описанию' }
      ]
    }
  },
  setup(props) {
    const { posts, totalPages, isPostsLoading } = usePosts(10)
    const { selectedSort, sortedPosts } = useSortedPosts(posts)
    const { searchQuery, sortedAndSearchedPosts } = useSortedAndSearchedPosts(sortedPosts)

    return {
      posts,
      totalPages,
      isPostsLoading,
      selectedSort,
      sortedPosts,
      searchQuery,
      sortedAndSearchedPosts
    }
  },
  methods: {
    async loadMorePosts() {
      try {
        this.page += 1
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
          params: {
            _page: this.page,
            _limit: this.limit
          }
        })
        this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit)
        this.posts = [...this.posts, ...response.data]
      } catch (e) {
        alert('Ошибка')
      }
    },
  }
}
</script>

<style>
.app__btns {
  display: flex;
  justify-content: space-between;
  margin: 15px 0;
}

.page__wrapper {
  display: flex;
  flex-direction: row;
  margin-top: 15px;
}

.page {
  border: 1px solid black;
  padding: 10px;
  cursor: pointer;
}

.current-page {
  border: 2px solid teal;
}

.observer {}
</style>
