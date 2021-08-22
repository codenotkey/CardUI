<template>
  <div>
    <TopNav/>
    <main>
      <h1>Card UI</h1>
      <h2>一个基于 VUE3.0 和卡片设计风格的UI组件库</h2>
      <p class="actions">
        <a href="https://github.com">GitHub</a>
        <router-link to="/doc">开始</router-link>
      </p>
    </main>
  </div>
</template>

<script>
import TopNav from '../components/TopNav.vue'
export default {
  name: 'Home',
  components: {TopNav}
}
</script>

<style lang="scss" scoped>
main {
  padding: 100px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: lightgreen;
  >h2{
    white-space:nowrap;
  }
  > .actions{
    padding: 8px 0;
    a {
      text-align: center;
      line-height: 4rem;
      font-size: 2rem;
      margin:12px;
      background: #fff;
      display: inline-block;
      height: 60px;
      width: 200px;
      border-radius: 56px;
    }
  }
}
</style>
