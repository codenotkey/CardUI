<template>
  <div class="navContent">
    <span class="toggleAside" @click="toggleAside"><img src="../assets/更多.png" alt=""/></span>
    <span class="logo">
      <router-link to="/" >
        <img src="../assets/卡片.png" alt="">
        <img src="../assets/logoT.png" alt="" class="logo2">
      </router-link>
    </span>
    <ul class="menu">
      <li><router-link to="/doc">文档</router-link> </li>
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
    padding: 15px 28px;
    display: flex;
    z-index: 10;
    justify-content: center;
    align-items: center;
    background: #f3f9ff;
    color: #5754d0;
    font-weight: bold;
    border-radius: 0 0 10px 10px;
    //box-shadow: 0 8px 12px #ebedf0;
    li{
      display: inline-block;
      margin-left: 12px;
    }
    .logo{
      margin-right: auto;
      img{
        height: 40px;
      }
      .logo2{
        margin-left: 10px;
        height: 40px;
        transform: scale(1.2);
      }
    }

    .toggleAside{
      display: none;
      >img{
        width: 28px;
      }
    }
    .menu{
      a{
        font-size: 20px;
      }
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
