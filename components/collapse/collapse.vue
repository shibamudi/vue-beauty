<template lang="html">

  <div class="ant-collapse">
    <slot></slot>
  </div>

</template>

<script>

import panel from './panel'

export default {
  name:'v-collapse',
  props: {
    accordion: {
      type: Boolean,
      default: false
    },
    activeKey: Array,
    defaultActiveKey: String,
    onChange: {
      type: Function,
      default: function (key) {
      }
    },
  },
  events: {
    'child-open': function (key) {
      if (this.accordion) {
        for (var panel of this.$children) {
          if (panel.key===key) {
            panel.open = true
          }else {
            panel.open = false
          }
        }
      }
      this.onChange(key)
    }
  },
  watch: {
    'activeKey': function () {
    }
  }
}
</script>
