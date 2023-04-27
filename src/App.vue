<template>
  <div>
    <div>Кол-во лайков: <strong>{{ likes }}</strong></div>
    <div>Кол-во дизлайков: <strong>{{ dislikes }}</strong></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      likes: 0,
      dislikes: 2,
    }
  }
}
</script>

<style>

</style>