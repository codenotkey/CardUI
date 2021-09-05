<template>
  <div>
    <TopNav/>
    <main>
      <h1>Card UI</h1>
      <h2>基于 VUE3.0 和卡片设计风格的UI组件库</h2>
      <p class="actions">
        <a href="https://github.com/codenotkey/CardUI">GitHub</a>
        <router-link to="/doc">开始</router-link>
      </p>
      <div class="bg"></div>
      <div class="bg"></div>
      <div class="bg"></div>
      <div class="bg"></div>
    </main>
    <footer class="features">
      <ul>
        <li>
          <img src="../assets/vue.png" alt="">
          <h3>基于 Vue 3</h3>
          <p>使用了 Vue 3 Composition API</p>
        </li>
        <li>
          <img src="../assets/ts.png" alt="">
          <h3>基于 Vue 3</h3>
          <p>源代码采用 TypeScript 书写（非严格检查）</p>
        </li>
        <li>
          <img src="../assets/简单.png" alt="">
          <h3>基于 Vue 3</h3>
          <p>每个组件的源代码都极其简洁</p>
        </li>
      </ul>
    </footer>
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
.bg{
  &:after{
    z-index: -1;
    width: 200px;
    height: 200px;
    content: '';
    background: #f9fcfe;
    position: absolute;
    top: 40%;
    left: -5%;
    box-shadow: 2px 2px 8px 0px rgb(189, 178, 178);
    animation: xx 2s infinite alternate;
    border-radius: 4px;
    opacity: 0.4;
  }
}
.bg+.bg{
  &:after{
    width: 200px;
    height: 200px;
    left: 30%;
    top: 20%;
    border-radius: 50%;
    animation: xx 2s 1s infinite alternate;
  }
}
.bg+.bg+.bg{
  &:after{
    left: 90%;
    top: 20%;
    width: 200px;
    height: 200px;
    background: #f8fbff;
    transform: rotateZ(45deg);
    animation: xx2 2s 2s infinite alternate;
    border-radius: 2px;
  }
}
.bg+.bg+.bg+.bg{
  &:after{
    left: 60%;
    top: -40%;
    width: 200px;
    height: 200px;
    background: #f8fbff;
    animation: xx 2s  infinite alternate;
    border-radius: 2px;
  }
}
@keyframes xx {
    from{
      transform: translateY(25px);
    }
    to{
      transform: translateY(0px);

    }
}

@keyframes xx2 {
  from{
    transform: rotateZ(45deg) translateY(25px);
  }
  to{
    transform: rotateZ(45deg) translateY(0px);
  }
}

main {
  z-index: 1;
  position: relative;
  background: #FFFFFF;
  padding:100px 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  animation:morph 2s linear infinite alternate;
  background: linear-gradient(to bottom,#f3f9ff,#eff8ff);
  overflow: hidden;
  >h1{
    color: #1a2b3b;
    font-size: 80px;
    font-weight: 600;
    text-align: center;
  }
  >h2{
    text-align: center;
  }
  > .actions{
    padding: 8px 0;
    a {
      //border: 0.5px solid #5754d0;
      text-align: center;
      line-height: 4rem;
      font-size: 2rem;
      margin:12px;
      background: #fff;
      display: inline-block;
      height: 60px;
      width: 200px;
      border-radius: 56px;
      color:#5754d0 ;
    }
  }
}
.features {
  margin: 80px auto;
  width: 400px;

  @media (min-width: 800px) {
    width: 800px;
  }

  @media (min-width: 1200px) {
    width: 1200px;
  }

  >ul {
    display: flex;
    flex-wrap: wrap;
    >li {
      width: 400px;
      margin: 16px 0;
      display: grid;
      justify-content: start;
      align-content: space-between;
      grid-template-areas:
        "icon title"
        "icon text";
      grid-template-columns: 80px auto;
      grid-template-rows: 1fr auto;

      >img {
        grid-area: icon;
        width: 64px;
        height: 64px;
      }

      >h3 {
        grid-area: title;
        font-size: 28px;
      }

      >p {
        grid-area: text
      }
    }
  }
}
</style>
