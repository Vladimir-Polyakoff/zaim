<template>
  <div id="app">
    <Header/>
      <Loader
      v-if="loading"
      />
      <div class="main" v-else>
        <div class="overlay" v-if="showPopular"></div>
        <div class="card__list" v-if="cards.length">
          <Card
            v-for="card in cards"
            :key="card.id"
            :card="card"
            @onClick="update"
          >
          </Card>
          <div class="footer__text">
            Сайт оказывает услуги по подбору кредитных продуктов для клиентов, а именно предлагает клиенту список предложений кредитных учреждений, некредитных финансовых организаций, в которые клиент может обратиться с целью оформления заявки на кредитный продукт. Проект не является банком или кредитором,
            не относится к финансовым учреждениям и не несёт ответственности за последствия любых заключенных договоров кредитования или условия по ним. Минимальная процентная ставка у некоторых
            партнеров составляет 0%.
          </div>
        </div>
        <NotFound
        v-else
        @reload="getList"
        />
      </div>

    <Banner
    v-if="cards.length"
    :submitedCount="submitedCount"
    @showPopularOffers="showPopular = true"
    />

    <PopularOffers
    v-if="showPopular"
    :list="[cards[0], cards[1]]"
    @onClick="update"
    @close="showPopular = false"
    />
  </div>
</template>

<script>
import Header from '@/components/Header'
import Card from '@/components/Card'
import Banner from '@/components/Banner'
import PopularOffers from '@/components/PopularOffers'
import NotFound from '@/components/NotFound'
import Loader from '@/components/Loader'

export default {
  components: {
    Header,
    Card,
    Banner,
    PopularOffers,
    NotFound,
    Loader
  },
  data () {
    return {
      cards: [],
      submitedCount: 0,
      showPopular: false,
      loading: false
    }
  },
  created () {
    this.getList()
  },

  methods: {
    getList () {
      this.loading = true
      fetch('https://i.helpzaim.ru/public-api/projects/1')
        .then(response => response.json())
        .then(({ successful, result }) => {
          if (successful) {
            this.cards = result.map(card => ({
              free: card.is_featured,
              ...card.offer,
              isClicked: false
            }))
          }
        })
        .finally(() => { this.loading = false })
    },

    update (id) {
      this.cards.forEach((card, index) => {
        if (card.id === id) {
          if (!card.isClicked) {
            this.submitedCount++
          }
          // без индекса вернте массив с тем удал,эл
          const clickedCard = this.cards.splice(index, 1)[0]
          clickedCard.isClicked = true
          this.cards.push(clickedCard)
          window.open(card.link, '_blank')
          this.showPopular = true
        }
      })
    }
  }
}
</script>

<style lang="scss">
#app {
  height: 100%;
  position: relative;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-bottom: 200px;
}
body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  background:  #dcd9e1;;
}
.overlay {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 1;
  background: rgba(0, 0, 0, 0.5);

}
.card__list {
  max-width: 1458px;
  position: absolute;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  gap: 8px;
  position: absolute;
  top: 221.5px;
    @media (max-width: 1460px) {
      // margin-inline:8px;
    }
    @media (max-width: 600px) {
      padding: 8px;
    }
    @media (max-width: 399px) {
      top: 253.5px
    }
    @media (max-width: 374px) {
      margin-top:46px;
      width: 100%;
    }
  & .footer__text {
    display: flex;
    flex-wrap: wrap;
    max-width: 1173px;
    font-family: 'Roboto';
    font-weight: 400;
    font-size: 10px;
    line-height: 16px;
    text-align: center;
    color: #73869D;
    padding-top: 48px;
    background: transparent;
    margin-inline: 128px;
    margin-top: 40px;
    margin-bottom: 500px;
    @media (max-width: 374px) {
      margin-inline: 20px;
    }
    @media (max-width: 399px) {
      margin-inline: 20px;
    }
  }
}
</style>
