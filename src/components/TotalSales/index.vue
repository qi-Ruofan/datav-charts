<template>
  <common-card :title="title" :value="value">
    <template>
      <div class="compare-wrapper">
        <div class="compare">
          <span>日同比</span>
          <span class="emphasis">7.33%</span>
          <span class="increase"></span>
        </div>
        <div class="compare">
          <span>日同比</span>
          <span class="emphasis">7.33%</span>
          <span class="decrease"></span>
        </div>
      </div>
    </template>
    <template v-slot:footer>
      <span>昨日销售额</span>
      <span class="emphasis">¥ 30,000,000</span>
    </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
  mixins: [commonCardMixin],
  data () {
    return {
      title: '累计销售额',
      value: '¥ 32,039,165'
    }
  }
  // created () {
  // },
  // methods: {
  // }
}
</script>

<style lang='scss' scoped>
.compare-wrapper {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .compare {
    display: flex;
    align-items: center;
    margin-top: 3px;
    font-size: 12px;
  }
}
</style>
