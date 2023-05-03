<template>
  <div class="navbar">
    <div @click="$router.push('/')" style="cursor: pointer;">Learning Vue</div>
    <div class="navbar__btns">
      <MyButton @click="$router.push('/')">Главная страница</MyButton>
      <MyButton style="margin-left: 20px;" @click="$router.push('/posts')">Посты</MyButton>
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
  background-color: lightgray;
  box-shadow: 2px 2px 4px gray;
  display: flex;
  align-items: center;
  padding: 0 15px;
}
.navbar__btns {
  margin-left: auto;
}
</style>