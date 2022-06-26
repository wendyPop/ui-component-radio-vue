<template>
  <div id="app">
    <section>
      <radio-button
          :items="radioData"
          :name="'가격필터'"
          :selected="selected"
          @check="clickPriceInfo"
      />
      <pre>
        <code>
          {{ priceSelected }}
        </code>
      </pre>
    </section>
  </div>
</template>

<script>
import RadioButton from './components/RadioButton.vue'

export default {
  name: 'App',
  data() {
    return {
      radioData: [
        {
          "nm": "전체",
          "min_dis_price": null,
          "max_dis_price": null,
          "is_editable": false
        },
        {
          "nm": "5만원 이하",
          "min_dis_price": 0,
          "max_dis_price": 50000,
          "is_editable": false
        },
        {
          "nm": "5만원 ~ 10만원 이하",
          "min_dis_price": 50000,
          "max_dis_price": 100000,
          "is_editable": false
        },
        {
          "nm": "10만원 ~ 50만원 이하",
          "min_dis_price": 100000,
          "max_dis_price": 500000,
          "is_editable": false
        },
        {
          "nm": "50만원 ~ 100만원 이하",
          "min_dis_price": 500000,
          "max_dis_price": 1000000,
          "is_editable": false
        }
      ],
      selected: 0,
      priceSelected: {
        name: '',
        minPrice: null,
        maxPrice: null,
      }
    }
  },
  components: {
    RadioButton
  },
  methods: {
    clickPriceInfo(value) {
      // 초기화
      this.priceSelected.name = ''
      this.priceSelected.minPrice = null
      this.priceSelected.maxPrice = null

      // 데이터 세팅
      const selected = this.radioData.find(v => v.nm === value)
      this.priceSelected.name = selected.nm
      this.priceSelected.minPrice = selected.min_dis_price
      this.priceSelected.maxPrice = selected.max_dis_price
    }
  }
}
</script>
