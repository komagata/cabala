<template>
  <div class="has-text-centered">
    <b-datepicker v-model="date" inline :first-day-of-week="1" placeholder="生年月日を選択してください" />
    <b-button class="submit" @click="submit">
      占う
    </b-button>
  </div>
</template>
<script>
export default {
  name: 'HomePage',
  data () {
    return {
      date: null
    }
  },
  computed: {
    destinyNumber () {
      return this.cabala(this.$dayjs(this.date).format('YYYYMMDD'))
    }
  },
  methods: {
    cabala (n) {
      const DESTINY_NUMBERS = [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 22]
      const number = Number(n)
      if (DESTINY_NUMBERS.includes(number)) {
        return number
      } else {
        return this.cabala(number.toString().split('').reduce((sum, s) => Number(sum) + Number(s), 0))
      }
    },
    submit () {
      if (!this.date) { return alert('生年月日を選択してください') }
      this.$router.push(`/numbers/${this.destinyNumber}`)
    }
  }
}
</script>
<style>
.submit {
  margin: 2em;
}
</style>
