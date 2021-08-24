<template>
  <div>
    <h1>这个是Button Page</h1>
    <hr>
    <div>
      <h1>按钮类型</h1>
      <Button level="primary" @click="handleX">主要按钮</Button>
      <Button >默认按钮</Button>
      <Button level="success">成功按钮</Button>
      <Button level="warn">警告按钮</Button>
      <Button level="danger">危险按钮</Button>
    </div>
    <div>
      <h1>按钮形状</h1>
      <Button level="primary">方形按钮</Button>
      <Button level="success" shape="rec" disabled>圆形按钮</Button>
    </div>
    <div>
      <h1>自定义背景和字体颜色</h1>
      <Button bg-color="linear-gradient(to right, rgb(255, 96, 52), rgb(238, 10, 36))" font-color="white">自定义颜色</Button>
    </div>
    <div>
      <h1>禁用按钮</h1>
      <Button level="primary" disabled>禁用按钮</Button>
    </div>
    <div>
      <h1>加载按钮</h1>
      <Button level="primary" loading>加载按钮</Button>
    </div>
  </div>
</template>

<script>
import Button from "../lib/Button.vue";
export default {
  name: 'Button.vue',
  components:{Button},
  setup(){
    const handleX=()=>{
      console.log('xxx')
    }
    return {handleX}
  }
}
</script>

<style scoped>
 div+div{
   margin-top: 20px;
 }
</style>
