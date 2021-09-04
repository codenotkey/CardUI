<demo>
自定义背景和字体颜色
</demo>
<template>
  <div>
    <Button bg-color="linear-gradient(to right, rgb(255, 96, 52), rgb(238, 10, 36))" font-color="white">自定义颜色</Button>
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
