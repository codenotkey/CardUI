<demo>
按钮形状
</demo>
<template>
  <div>
    <Button level="primary">方形按钮</Button>
    <Button level="success" shape="rec" disabled>圆形按钮</Button>
  </div>
</template>

<script lang="ts">
import Button from "../lib/Button.vue";
export default {
  components: {
    Button
  }
}
</script>
