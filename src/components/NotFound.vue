<template>
  <div>
    <h1>Не удалось загрузить данные</h1>
    <h3 @click="$emit('reload')">Пробовать снова</h3>
  </div>
</template>

<script>
export default {
  name: 'NotFound'
}
</script>

<style scoped>
  div {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction:column;
  }
  h3 {
    cursor:pointer;
    color: rgba(47, 47, 159, 0.441);
  }
</style>
