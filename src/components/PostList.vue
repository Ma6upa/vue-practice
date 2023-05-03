<template>
  <div v-if="posts.length > 0">
    <h3>Список постов</h3>
    <TransitionGroup name="post-list">
      <PostItem 
        v-for="post in posts" 
        :post="post" 
        :key="post.id"
        @remove="$emit('remove', post)"
      />
    </TransitionGroup>
  </div>
  <h2 v-else>
    Списпок постов пуст
  </h2>
</template>

<script>
import { TransitionGroup } from 'vue';
import PostItem from './PostItem.vue';

export default {
  props: {
    posts: {
      type: Array,
      required: true
    }
  },
  components: { PostItem, TransitionGroup }
}
</script>

<style scoped>
.post-list-enter-active,
.post-list-leave-active {
  transition: all 0.3s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.post-list-move {
  transition: transform 0.5s ease
}
</style>
