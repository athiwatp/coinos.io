<template lang="pug">
.tippad.text-xs-right(style='direction: rtl')
  span #[span.display-1 {{tip}}]+
  v-layout(wrap style='direction: ltr')
    v-flex
      v-btn(:class='percent === 0 && "secondary"' @click='percent = 0') No Tip
      v-btn(:class='percent === 10 && "secondary"' @click='percent = 10') +10%
    v-flex
      v-btn(:class='percent === 15 && "secondary"' @click='percent = 15') +15%
      v-btn(:class='percent === 20 && "secondary"' @click='percent = 20') +20%
</template>

<script>
export default {
  props: {
    amount: {
      type: Number,
      default: 0,
    },
  },

  data () {
    return {
      percent: 0,
    }
  },

  computed: {
    tip () {
      let tip = (this.percent * this.amount * 0.01).toFixed(2)
      this.$emit('update', tip)
      return tip
    },
  },
}
</script>

<style lang="stylus" scoped>
.v-btn
  margin-right: 0;
  min-width: auto;
  width: 95%;
</style>
