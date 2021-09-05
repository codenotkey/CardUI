<template>
  <div class="layout">
    <TopNav  class="nav"/>
    <div class="content">
      <aside v-if="asideVisible">
        <h1>文档</h1>
        <ul>
          <li><router-link to="/doc/intro">介绍</router-link></li>
          <li><router-link to="/doc/install">安装</router-link></li>
          <li><router-link to="/doc/get-started">开始使用</router-link></li>
        </ul>
        <h1>组件列表</h1>
        <ul>
          <li><router-link to="/doc/button">Button 组件</router-link></li>
          <li><router-link to="/doc/switch">Switch 组件</router-link></li>
          <li><router-link to="/doc/dialog">Dialog 组件</router-link></li>
          <li><router-link to="/doc/tabs">Tabs 组件</router-link></li>
        </ul>
      </aside>
      <main>
        <router-view/>
      </main>
    </div>
  </div>
</template>

<script lang="ts">
import TopNav from '../components/TopNav.vue'
import { inject, Ref } from "vue";

export default {
  components: {TopNav},
  setup(){
    const asideVisible = inject<Ref<boolean>>('asideVisible')
    console.log(asideVisible);
    return {asideVisible}
  }
}
</script>

<style lang="scss" scoped>
.layout{
  display: flex;
  background: #f6f8f9;
  flex-direction: column;
  height: 100vh;
  > .nav {
    flex-shrink: 0;
  }
  .content{
    flex-grow: 1;
    display: flex;
    aside{
      text-align: center;
      padding: 0 20px;
      white-space: nowrap;
      flex-shrink: 0;
      background: linear-gradient(to bottom,#f3f9ff,#eff8ff);
      ul{
        margin-bottom: 20px;
      }
      >ul>li{
        font-family: PingFangSC;
        font-size: 14px;
        border-radius: 56px ;
        background: #FFFFFF;
        margin-top: 10px;
        >a {
          border-radius: 56px ;
          padding: 15px 20px;
          display: block;
          text-decoration: none;
          font-family: "Segoe UI";
        }
        .router-link-active {
          background: #5754d0;
          color:  white;
          transition: all .3s ease-in-out;
        }
      }
    }
    main{
      flex-grow: 1;
      border-radius: 40px;
      background: white;
      padding: 40px 0 0 40px;
    }
    @media (max-width: 500px) {
      main{
        padding: 10px 0 0 10px;
      }
      aside{
          padding: 0 8px;
      }
    }
  }
}
</style>
