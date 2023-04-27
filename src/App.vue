<template>
  <div>
    <div class="post" v-for="post in posts">
      <div><strong>Название: </strong> {{ post.title }} </div>
      <div><strong>Описание: </strong> {{ post.body }} </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'JS - язык программирования'},
        {id: 2, title: 'Чай', body: 'Чай - единственный допустимый напиток'},
        {id: 3, title: 'УдГУ', body: 'УдГУ - вроде как вуз'},
      ]
    }
  },
  methods: {
    
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 10px;
}
</style>