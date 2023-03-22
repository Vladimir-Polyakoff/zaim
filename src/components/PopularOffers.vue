<template>
  <div class="offer">
    <div class="offer__header">
      <div class="close"
      @click="$emit('close')"
      >+</div>

      <div class="title">Популярные предложения</div>

      <div class="description">Мы подготовили для вас самые выгодные<br> микрозаймы, чтобы вы не тратили <br>время на поиск</div>
    </div>

    <div class="offer__body">
      <Card
        v-for="(card, index) in list" :key="index"
        :card="card"
        @onClick="id => $emit('onClick', id)"
      >
      </Card>
    </div>
  </div>
</template>

<script>
import Card from '@/components/Card'

export default {
  name: 'PopularOffers',
  components: {
    Card
  },
  props: {
    list: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
  .offer {
    position: fixed;
    bottom: 0;
    z-index: 11;
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    @media (max-width: 399px) {
      bottom: 0px;
      border-radius: 16px 16px 0px 0px;
    }
    @media (max-width: 374px) {
      bottom: 0px;
      border-radius: 16px 16px 0px 0px;
    }
    &__header {
      position: relative;
      width: inherit;
      text-align: center;
      align-self: left ;
      padding-block: 16px;
      background: #FFFFFF;
      border-radius: 16px 16px 0px 0px;
      @media (max-width: 374px) {
        border-radius: 16px 16px 0px 0px;
      }
    }
  }
  .title {
    font-weight: 700;
    font-size: 16px;
    line-height: 24px;
    text-align: center;
    color: #000000;
      @media (max-width: 399px) {
        width: 100%;
        margin-bottom: -10px;
        margin-top: -4px;
      }
    @media (max-width: 374px) {
      width: 100%;
      margin-bottom: -10px;
      margin-top: -4px;
    }
  }
  .description {
    font-weight: 400;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    color: #000000;
    margin:16px auto;
    width: 360px;
    @media (max-width: 399px) {
      width: 100%;
      margin-bottom: -4px;
    }
    @media (max-width: 374px) {
      width: 100%;
      margin-bottom: -4px;
    }
  }
  .offer__body {
    background:  #dcd9e1;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 16px;
    padding: 24px;
      @media (max-width: 399px) {
        padding: 16px 8px;
        gap: 8px;
      }
      @media (max-width: 600px) {
        padding: 16px 8px;
        gap: 8px;
      }
    @media (max-width: 374px) {
      padding: 16px 8px;
      gap: 8px;
    }
  }
  .close {
    position: absolute;
    padding: 16px;
    transform: rotate(45deg);
    top: 0px;
    right: 0px;
    font-weight: 900;
    font-size: 30px;
    cursor: pointer;
    user-select: none;
    @media (max-width: 374px) {
      top: -8px;
      right: -8px
    }
  }
</style>
