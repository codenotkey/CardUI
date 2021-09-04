<template>
  <div>
    <Demo :component="Switch1Demo" />
    <Demo :component="Switch2Demo" />
  </div>
</template>

<script lang="ts">
import Switch from '../lib/Switch.vue'
import {ref}  from 'vue'
import Switch1Demo from './Switch1.demo.vue'
import Switch2Demo from './Switch2.demo.vue'
import Demo from './Demo.vue'
export default {
  name: 'SwitchDemo',
  components:{Switch,Demo},
  setup(){
    const bool = ref(false)
    return {Switch1Demo,Switch2Demo}
  }
}
</script>

<style scoped>

</style>
