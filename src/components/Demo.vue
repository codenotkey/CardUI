<template>
  <div class="demo">
    <h2>{{component.__sourceCodeTitle}}</h2>
    <div class="demo-component">
      <component :is="component" />
    </div>
    <div class="demo-actions">
      <Button level="primary" shape="rec" @click="toggleCode">查看代码</Button>
    </div>
    <div class="demo-code" v-if="codeVisible">
      <pre class="language-html" v-html="html" />
    </div>

  </div>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'
import 'prismjs';
import 'prismjs/themes/prism-solarizedlight.css'
import {
  computed,
  ref
} from 'vue';
const Prism = (window as any).Prism
export default {
  components: {
    Button
  },
  props: {
    component: Object
  },
  setup(props) {
    const html = computed(() => {
      return Prism.highlight(props.component.__sourceCode, Prism.languages.html, 'html')
    })
    const toggleCode = () => codeVisible.value = !codeVisible.value
    const codeVisible = ref(false)
    return {
      Prism,
      html,
      codeVisible,
      toggleCode
    }
  }
}
</script>

<style lang="scss" scoped>
$border-color: #d9d9d9;

.demo {
  padding: 24px;
  margin: 16px 50px 35px 0;
  border-radius: 20px;
  box-shadow: 0 8px 12px #ebedf0;
  >h2 {
    color: #323233;
    font-weight: 600;
    font-size: 20px;
    padding: 8px 16px;
    //border-bottom: 1px solid $border-color;
  }

  &-component {
    padding: 16px;
  }

  &-actions {
    padding: 8px 16px;
    //border-top: 1px dashed $border-color;
  }

  &-code {
    padding: 8px 0px;
    border-top: 1px dashed $border-color;
    >pre {
      font-family: sfmono-regular,Consolas,liberation mono,Menlo,Courier,monospace;
      line-height: 1.4;
      margin: 0;
      background: #f8f8f8;
      border-radius: 20px;
    }
  }
}
</style>
