<template>
  <div class="header">
        <div class="approve">
            <div class="approve__head--title">МФО с наибольшим количеством одобрений на {{ getDateNow }}</div>
            <img class="approve__img" src="@/image/header-like.svg" alt="like">
            <div class="approve__title">Вам одобрили займ!</div>
            <div class="approve__content">Выберите подходящие Вам условия
              и оформите займ
            </div>
        </div>
  </div>
</template>

<script>
export default {
  name: 'TheHeader',
  computed: {
    getDateNow () {
      const now = new Date()
      const date = now.getDate()
      const month = now.getMonth() + 1

      return `${date < 10 ? '0' + date : date}.${month < 10 ? '0' + month : month}.${now.getFullYear()}`
    }
  }
}
</script>

<style scoped lang="scss">
  .header {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 364px;
    width: 100%;
    background:url(../image/header-money.png);
    background-color: rgb(58 56 79);
    background-blend-mode: multiply;
  }
    .approve {
        position: absolute;
        top: 8px;
        font-family: 'Open Sans';
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        // через deefore like
      &__head--title {
        font-weight: 400;
        font-size: 14px;
        line-height: 20px;
        text-align: center;
        color: #FFFFFF;
        margin-bottom: 24px;
        @media (max-width: 374px) {
          margin-inline: 32px;
        }
        @media (max-width: 399px) {
          margin-inline: 52px;
        }
      }
      &__img {
        margin-bottom: 16px;
        width: 64px;
        height: 64px;
      }
      &__title {
        width: 280px;
        height: 32px;
        font-weight: 700;
        font-size: 24px;
        line-height: 32px;
        text-align: center;
        color: #FFFFFF;
        margin-bottom: 16px;
      }
      &__content {
        width: 280px;
        height: 40px;
        font-weight: 400;
        font-size: 14px;
        line-height: 20px;
        text-align: center;
        color: #FFFFFF;
        margin-bottom: 36px;
      }
    }
</style>
