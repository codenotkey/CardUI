<template>
  <router-view/>
</template>

<script lang="ts">
import {router} from "./router";
import { ref, provide } from "vue";

export default {
  name: 'App',
  setup(){
    const width = document.documentElement.clientWidth
    const asideVisible = ref(width > 500)
    provide('asideVisible',asideVisible)
    router.afterEach(()=>{
      if (width<=500){
        asideVisible.value = false
      }
    })
  }
}
</script>
