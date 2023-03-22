<template>
  <div class="banner">
    <div class="banner__container">
      <div class="banner__title">
        Отправлено {{ submitedCount }} из 3 заявок
      </div>

      <div class="banner__progress">
        <span :style="submitedCount && 'background: #10C698;'"></span>
        <span :style="submitedCount > 1 && 'background: #10C698'"></span>
        <span :style="submitedCount > 2 && 'background: #10C698'"></span>
      </div>

      <div class="banner__description">
        Для получения персонального предложения со 100% одобрением отправьте заявку в 3 компании
      </div>

      <button :style="submitedCount > 2 && 'background: #10C698'"
        @click="showPopularOffers"
      >{{ buttonTitle }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TheBanner',
  props: {
    submitedCount: {
      type: Number,
      required: true
    }
  },
  computed: {
    buttonTitle () {
      return this.submitedCount < 3 ? `Выбрано ${this.submitedCount} из 3` : 'Получить'
    }
  },
  methods: {
    showPopularOffers () {
      this.submitedCount > 2 && this.$emit('showPopularOffers')
    }
  }
}
</script>

<style scoped lang="scss">
  .banner {
    position: fixed;
    bottom: 0;
    width: 100%;
    padding-block: 24px;
    background: #fff;
    display: flex;
    justify-content: center;
    border-radius: 16px 16px 0px 0px;
    @media (max-width: 374px) {
      border-radius: 16px 16px 0px 0px;
      bottom: -10px;
    }

    &__container {
      // display: flex;
      // flex-direction: column;
      // align-items: center;
      text-align: center;
      width: 450px;
      @media (max-width: 374px) {
          width: 320px;
        }
    }

    // banner__title
    &__title {
      font-weight: 700;
      font-size: 16px;
      line-height: 24px;
      text-align: center;
      color: #000000;
      @media (max-width: 374px) {
          font-size: 14px;
        }
    }

    &__progress {
      margin-block: 16px;
      display: flex;
      justify-content: center;
      span {
        width: 110.29px;
        height: 8px;
        background: #73869d4e;
        border-radius: 4px;
        margin-inline: 8px;
        @media (max-width: 399px) {
          margin-inline: 5px;
          width: 93px;
        }
        @media (max-width: 374px) {
          margin-inline: 5px;
          width: 93px;
        }
      }
    }

    &__description {
      font-weight: 400;
      font-size: 14px;
      line-height: 20px;
      text-align: center;
      color: #000000;
      margin-bottom: 12px;
      @media (max-width: 600px) {
          margin-inline: 30px;
        }
      @media (max-width: 399px) {
          margin-inline: 20px;
        }
      @media (max-width: 374px) {
        font-size: 12px;
        line-height: 16px;
        }
    }

    button {
      width: 343px;
      height: 48px;
      left: 549px;
      top: 809px;
      background: #73869d4e;
      border-radius: 8px;
      font-style: normal;
      font-weight: 600;
      font-size: 16px;
      line-height: 24px;
      text-align: center;
      color: #2D3A4A;
      border: none;
      @media (max-width: 374px) {
        width: 288px;
        height: 48px;
        }
      @media (max-width: 399px) {
        width: 288px;
        height: 48px;
        }
    }

  }
</style>
