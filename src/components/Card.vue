<template>
  <div class="card" @click="$emit('onClick', card.id)">
    <div class="card__title">
      <img :src="card.logo" alt="">
    </div>
    <!-- <div v-if="card.free" class="card__free">Первы займ <span>бесплатно!</span></div> -->
    <div class="card__free-line"></div>
    <div class="card__container-percent">
      <div class="sum">
        <div class="title">Макс. сумма до:</div>
        <div class="amount">{{ card.header }}<span>₽</span></div>
      </div>
      <div class="bid">
        <div class="title">Ставка:</div>
        <div class="percent">{{ Number(!card.free) }}%</div>
        <!-- <div class="percent">{{ card.free ? '0' : '1' }}%</div> -->
      </div>
    </div>
    <div v-if="card.sub_header" class="age__valid">{{card.sub_header}}</div>
    <button :style="card.isClicked && 'background: #73869d4e'" >Получить деньги</button>
  </div>

</template>

<script>
export default {
  name: 'TheCards',
  props: {
    card: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
  .card {
    // margin-bottom: -34px;
    // margin-top: 36px;
    box-sizing: border-box;
    width: 174px;
    height: 268px;
    left: 0px;
    top: 0px;
    background: #FFFFFF;
    box-shadow: 0px 16px 32px rgba(0, 0, 0, 0.25);
    border-radius: 16px;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
      @media (max-width: 374px) {
        width: 148px;
        height: 259px;
        padding-block: 10px;
      }
      @media (max-width: 399px) {
        width: 148px;
        height: 259px;
        padding-block: 10px;
      }
    &__title img{
      width: 120px;
      height: 40px;
      display: flex;
      justify-content: center;
      align-items: center;
      user-select: none;
      padding: 12px;
      scale: 0.8;
      @media (max-width: 374px) {
        padding-block: 0px;
      }
      @media (max-width: 399px) {
        padding-block: 0px;
      }
    }
    &__free-line {
      width: 100%;
      height: 1px;
      background: #D1D1D6;
      margin-bottom: 16px;
      }
    // &__free {
    //   width: 100%;
    //   height: 1px;x
    //   font-family: 'Rubik';
    //   font-style: normal;
    //   font-weight: 400;
    //   font-size: 14px;
    //   line-height: 20px;
    //   text-align: center;
    //   color: #FFFFFF;
    //   background: linear-gradient(180deg, #FF801A 0%, #FF9A00 100%);
    //   text-shadow: 0px 1px 0px rgba(0, 0, 0, 0.14);
    //   display: flex;
    //   align-items: center;
    //   justify-content: center;
    //   margin-bottom:8px ;
    //     span {
    //       margin: 0 4px;
    //       text-transform: uppercase;
    //       font-weight: 800;
    //     }
    //   }
    &__container-percent {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      .sum {
        .title {
          text-align: center;
          font-weight: 400;
          font-size: 10px;
          line-height: 14px;
          color: #828282;
      }
        .amount {
          text-align: center;
          font-family: 'Open Sans';
          font-weight: 700;
          font-size: 32px;
          line-height: 24px;
          color: #1C1C1E;
          margin-bottom: 8px;
          @media (max-width: 374px) {
            margin-bottom: 6px;
          }
          @media (max-width: 399px) {
            margin-bottom: 6px;
          }
          span {
            font-family: 'Roboto';
            font-weight: 400;
            font-size: 32px;
            line-height: 32px;
            color: #636366;
            margin-left: 7px;
          }
        }
      }
      .bid {
        text-align: center;
        margin-bottom: 8px;
        .title {
          font-family: 'Rubik';
          font-weight: 400;
          font-size: 12px;
          line-height: 14px;
          color: #828282;
        }
      .percent {
          font-family: 'Open Sans';
          font-weight: 700;
          font-size: 32px;
          line-height: 32px;
          color: #FF3B30;
        }
        @media (max-width: 374px) {
          font-size: 24px;
          margin-bottom: 6px;
        }
        @media (max-width: 399px) {
          font-size: 24px;
          margin-bottom: 6px;
        }
      }
    }
      & .age__valid {
        font-family: 'Rubik';
        font-weight: 400;
        font-size: 10px;
        line-height: 16px;
        text-align: center;
        color: #828282;
        margin-bottom: 8px;
        @media (max-width: 374px) {
          margin-bottom: 6px;
        }
        @media (max-width: 399px) {
          margin-bottom: 6px;
        }
      }
    button {
      width: 150px;
      height: 40px;
      background: #10C698;;
      box-shadow: 0px 10px 20px rgba(59, 179, 142, 0.25);
      border-radius: 8px;
      border: none;
      font-family: 'Montserrat';
      font-weight: 400;
      font-size: 16px;
      line-height: 24px;
      text-align: center;
      color: #FFFFFF;
      text-shadow: 0px 1px 3px #0EA781;
      margin: 0 12px 12px;
        @media (max-width: 374px) {
          width: 132px;
          height: 20x;
          margin: 0px;
        }
        @media (max-width: 399px) {
          width: 132px;
          height: 20x;
          margin: 0px;
        }
      }
  }

</style>
