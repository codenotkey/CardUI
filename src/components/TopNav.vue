<template>
  <div class="navContent">
    <span class="toggleAside" @click="toggleAside">更多</span>
    <span class="logo">LOGO</span>
    <ul class="menu">
      <li>菜单一</li>
      <li>菜单二</li>
    </ul>
  </div>
</template>

<script lang="ts">
import {inject,Ref} from 'vue'

export default {
  setup(){
    const asideVisible = inject<Ref<boolean>>('asideVisible')
    const toggleAside =()=>{
      asideVisible.value = !asideVisible.value
    }
    return {toggleAside}
  }
}
</script>

<style  lang="scss" scoped>
  .navContent{
    padding: 30px 28px 20px;
    display: flex;
    z-index: 10;
    justify-content: center;
    align-items: center;
    background: #f6f8f9;
    color: #5754d0;
    li{
      display: inline-block;
      margin-left: 12px;
    }
    .logo{
      margin-right: auto;
    }
    .toggleAside{
      display: none;
    }
    @media (max-width: 500px) {
      .toggleAside{
        display: inline-block;
      }
      .logo{
        margin: 0 auto;
      }
      .menu{
        display: none;
      }
    }
  }
</style>
