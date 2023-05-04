<template>
  <div class="navbar">
    <div @click="$router.push('/')" style="cursor: pointer; color: white">
      <h1>Learning Vue</h1>
    </div>
    <div class="navbar__btns">
      <MyButton @click="$router.push('/')" class="navbar__btn">Главная страница</MyButton>
      <MyButton style="margin-left: 20px;" @click="$router.push('/posts')" class="navbar__btn">Посты</MyButton>
      <MyButton style="margin-left: 20px;" @click="$router.push('/posts_with_hooks')" class="navbar__btn">Посты на хуках</MyButton>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
}
</script>

<style scoped>
.navbar {
  height: 50px;
  background-color: teal;
  box-shadow: 2px 2px 4px gray;
  display: flex;
  align-items: center;
  padding: 0 15px;
}
.navbar__btns {
  margin-left: auto;
}

.navbar__btn {
  color: white;
  border: 1px solid white;
}
</style>