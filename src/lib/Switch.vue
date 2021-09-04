<template>
    <button class="card-swc-btn" @click="toggle" :class="{checked:value}">
      <div class="card-swc-bg"></div>
      <span class="card-swc-circle" ></span>
    </button>
</template>

<script >
export default {
  name: 'switch',
  props:{
    value:Boolean
  },
  setup(props,context){
      const toggle= () =>{
        context.emit('update:value',!props.value)
    }
    return {toggle}
  }
}
</script>

<style lang="scss">
  $h:30px;
  $w:60px;
  $h2: $h - 2px;
  .card-swc-btn{
    display: inline-block;
    height: $h;
    width: $w;
    border: none;
    border-radius: $h;
    position: relative;
    overflow: hidden;
    &:focus{
      outline: none;
    }
    .card-swc-bg{
      position: absolute;
      display: inline-block;
      height: $h2;
      width: $h2 - 2px;
      border-radius: $h2;
      left: 2px;
      top: 1px;
      background: #fff;
      z-index: 1;
      transition: all 250ms ease-in-out;
    }
    .card-swc-circle{
      z-index: 2;
      width: $h2;
      height: $h2;
      border-radius: $h2;
      background: #fff;
      position: absolute;
      left: 1px;
      top: 1px;
      transition: all 250ms ease-in-out;
    }
    &.checked{
      >.card-swc-bg{
        background: #5754d0;
        width: calc(100% - 4px)
      }
      >.card-swc-circle{
        left: calc(100% - #{$h2} - 1px)
      }
    }

  }
</style>
