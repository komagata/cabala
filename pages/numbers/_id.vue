<template>
  <div class="card article">
    <div class="card-content">
      <div class="content">
        <p>あなたの運命数は<span class="destiny-number">{{ destiny.id }}</span>です。</p>
        <h2>性格</h2>
        <p>{{ destiny.character }}</p>
        <h2>マイナス面</h2>
        <p>{{ destiny.negative }}</p>
        <h2>恋愛と結婚</h2>
        <p>{{ destiny.love }}</p>
        <h2>相性</h2>
        <p>{{ destiny.chemistry }}</p>
        <h2>仕事</h2>
        <p>{{ destiny.work }}</p>
        <h2>適職</h2>
        <p>{{ destiny.job }}</p>
        <h2>金運</h2>
        <p>{{ destiny.money }}</p>
        <h2>有名人</h2>
        <p>{{ destiny.person }}</p>
      </div>
    </div>
  </div>
</template>
<script>
import destinies from '@/assets/json/destinies.json'

export default {
  name: 'NumbersIndex',
  computed: {
    destiny () {
      return destinies.find(destiny => destiny.id === Number(this.$route.params.id))
    }
  },
  methods: {
  }
}
</script>
<style>
</style>
